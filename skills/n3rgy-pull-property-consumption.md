---
generated: '2026-07-27'
method: generated
name: Pull half-hourly consumption for a consented property
description: >-
  Walk from an API key to a half-hourly electricity or gas consumption series for
  one GB property, handling the consent gate and the cache window correctly.
api: openapi/n3rgy-customer-service-api-v2-openapi.yaml
operations: [RetrieveConsentedMPxNs, RetrieveConsentedMPxNUtilities, RetrieveDataTypesForUtility, RetrieveDataForReadingType]
source: >-
  Every operationId verified verbatim in
  openapi/n3rgy-customer-service-api-v2-openapi.yaml. Semantics from
  https://customer-api-user-manuals.data.n3rgy.com/requests/.
---

# Pull half-hourly consumption for a consented property

The canonical n3rgy flow: discover what you have consent for, confirm the property actually has the utility and reading type you want, then pull the series.

## Auth

- Send `x-api-key: <key>` on every request. The key must have been enabled by the n3rgy back office — see `authentication/n3rgy-authentication.yml`.
- Base URL is the environment: `https://api-v2-sandbox.data.n3rgy.com` for testing, `https://api-v2.data.n3rgy.com` for live. There are no key prefixes; the host is the switch.

## Steps

1. **List what you have consent for** — `RetrieveConsentedMPxNs` (`GET /`). Optional `startat` / `maxresults` (default and maximum 100). Read `total` and `entries[]`; page with `startat` until you have collected `total` MPxNs. Entries are ordered by consent date, most recent first.
2. **Confirm the utility exists on that HAN** — `RetrieveConsentedMPxNUtilities` (`GET /mpxn/{mpxn}`). Returns the utilities (electricity, gas) with meters on the Home Area Network behind that MPxN.
3. **Confirm the reading type is available** — `RetrieveDataTypesForUtility` (`GET /mpxn/{mpxn}/utility/{utility}`). `utility` is `electricity` or `gas`.
4. **Pull the series** — `RetrieveDataForReadingType` (`GET /mpxn/{mpxn}/utility/{utility}/readingtype/{readingType}`).
   - `readingType` = `consumption` (import) or `production` (export).
   - `start` / `end` accept `yyyyMMddHHmmss`, `yyyyMMddHHmm` or `yyyyMMdd`. Defaults are yesterday 00:30 to today 00:00.
   - `granularity` is `halfhour` (default) or `day`.
   - `outputFormat` is `json` (default) or `csv`.
5. **Trust `availableCacheRange`, not your request window.** The response carries `availableCacheRange {start, end}` — the range n3rgy actually holds. Clip your expectations to it before charting or billing off the series.

## The MPxN is a handle for the HAN, not the meter

The guide is explicit: the MPxN only identifies the Home Area Network. You may legitimately pass an MPRN while asking for `utility=electricity`. Do not "correct" a caller's MPxN to match the utility.

## Errors that mean something specific

- `403 "Consent for the given MPxN not found."` — you have a valid key but no active consent for that property. This is a consent gap, not an auth failure. Do not retry; the occupant must grant consent in the n3rgy Consumer Portal.
- `403 "Consent for the given MPxN does not have update frequencies set."` — consent exists, but every update frequency was set to `never`. Fix with `SetMeterUpdateFrequency` for the one utility/reading type you need (see the `n3rgy-fix-never-update-frequency` skill).
- `403 "User is not authorized to access this resource with an explicit deny."` — bad or absent `x-api-key`.
- `400 "An MPxN must be provided, and must be a value between 1 and 13."` — MPxN must be 1-13 digits.
- `404` on step 3 means the utility has no meter on that HAN.

Full catalogue: `errors/n3rgy-problem-types.yml`. Errors are a proprietary `{"errors":[{"code","message"}]}` envelope — match on `message`, not on a symbolic code, because there isn't one.

## Notes

- Readings are served from n3rgy's cache, refreshed at the property's configured update frequency. A 200 is "here is the cache", not "here is a live meter read".
- A reading the meter reports above the maximum allowed comes back as the literal string `"invalid value"` — filter it before aggregating.
- There is no `Idempotency-Key` contract; these are all GETs, so retries are safe. See `conventions/n3rgy-conventions.yml`.
- Sandbox fixtures with pre-granted consent are in `sandbox/n3rgy-sandbox.yml` (e.g. MPxN `1234567891000`).
