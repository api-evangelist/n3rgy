---
generated: '2026-07-27'
method: generated
name: Unblock a property whose update frequencies are set to never
description: >-
  Diagnose and repair the most common n3rgy 403 — consent exists but the reading
  type's update frequency is "never", so no data will ever be returned.
api: openapi/n3rgy-customer-service-api-v2-openapi.yaml
operations: [RetrieveDataUpdateFrequencies, SetMeterUpdateFrequency, SetDefaults, ResetAllUpdateFrequencies, RetrieveMPxNAvailability]
source: >-
  Every operationId verified verbatim in
  openapi/n3rgy-customer-service-api-v2-openapi.yaml. Semantics and the exact
  error strings from https://customer-api-user-manuals.data.n3rgy.com/requests/.
---

# Unblock a property whose update frequencies are set to never

If a property returns `403 "Consent for the given MPxN does not have update frequencies set."` — or a data call for one reading type 403s while another works — the occupant consented but chose `never` for that reading type. n3rgy will never collect it until the frequency changes.

## Auth

- `x-api-key` header, plus an active consent for the HAN, plus — for every write here — the account permission to change update frequencies. All three failures return 403 with the same "explicit deny" message. See `authentication/n3rgy-authentication.yml`.

## Steps

1. **Read the current state** — `RetrieveDataUpdateFrequencies` (`GET /get-update-frequencies/{mpxn}`). Shows the update frequency per utility on that HAN.
2. **Find the device id** — `RetrieveMPxNAvailability` (`GET /find-mpxn/{identifier}`) returns `deviceId`, `deviceType`, `deviceStatus`, manufacturer/model and firmware for the meter behind that MPxN. You need `deviceId` for the next step.
3. **Change only the frequency you need** — `SetMeterUpdateFrequency` (`PUT /set-meter-update-frequency`). Body takes `deviceID` plus `importUpdateFrequency` and/or `exportUpdateFrequency`. The guide is emphatic that you only need to change the one corresponding to the utility/reading type you want.
4. **Re-run the data call.** The 403 clears once a non-`never` frequency is set and the next collection runs.

## Broader levers (use with care)

- `SetDefaults` (`PUT /set-defaults`) sets the ACCOUNT-level defaults applied to new consents: `getHistoryData`, `electricityImportUpdateFrequency`, `electricityExportUpdateFrequency`, `gasUpdateFrequency`, plus the instantaneous-register and daily-read-log variants. It does not retro-fix existing consents.
- `ResetAllUpdateFrequencies` (`PUT /reset-all-update-frequencies`) FORCES the new frequencies across **every already-consented HAN** on the account. Estate-wide blast radius — confirm with a human before calling it.

## Frequency values

Canonical enum for `set-defaults` and `reset-all-update-frequencies`: `NEVER`, `H_2`, `H_6`, `H_12`, `DAILY`, `WEEKLY`, `MONTHLY`.

The `set-meter-update-frequency` page documents the lower-case form (`never`, `3h`, `6h`, `12h`, `daily`, `weekly`, `monthly`) and its own error message lists `2h` as well — the guide is internally inconsistent here. Send the value the endpoint's own page documents, and treat a `400 Parameter "..." must be one of: ...` as authoritative for that endpoint.

## Getting history the caller thought they'd lost

There is no endpoint for it. If the occupant originally consented with `getHistoryData` false and now wants pre-consent data, they **re-consent the same MPxN with `getHistoryData` true** — no withdrawal first. That alone triggers the historical backfill.

## Errors

- `400 "One device ID and at least one update frequency must be provided."`
- `400 "The specified deviceID does not correspond to a meter."` — you passed a CHF/GPF/IHD id.
- `404 "The specified deviceID is not associated with a valid MPxN for the requested update frequency type."` — e.g. asking for an export frequency on a meter with no export MPAN.
- `403 "Consent for the property of the target meter not found."`

Full catalogue: `errors/n3rgy-problem-types.yml`.

## Notes

- All three writes are PUTs and are naturally idempotent; n3rgy publishes no idempotency-key contract. See `conventions/n3rgy-conventions.yml`.
- Setting a reading type to `never` does NOT return an empty series later — it returns 403. Consent, not data, is the gate.
