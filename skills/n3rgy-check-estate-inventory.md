---
generated: '2026-07-27'
method: generated
name: Run a DCC device inventory across a portfolio of properties
description: >-
  Batch the asynchronous Read Inventory job over up to 200 MPxNs, UPRNs or device
  IDs, poll the result URI, and stay inside the published quotas.
api: openapi/n3rgy-customer-service-api-v2-openapi.yaml
operations: [ReadInventory, RetrieveMPxNAvailability, mpxnFromAddress]
source: >-
  Every operationId verified verbatim in
  openapi/n3rgy-customer-service-api-v2-openapi.yaml. Timing, quota and retention
  behaviour from https://customer-api-user-manuals.data.n3rgy.com/requests/.
---

# Run a DCC device inventory across a portfolio of properties

`ReadInventory` returns the DCC's own device inventory (device data plus WAN matrix) for a set of properties. It is the estate-health workhorse — and the one operation where getting the async and quota behaviour wrong is expensive.

## Auth

- `x-api-key` only. No consent check on this operation. See `authentication/n3rgy-authentication.yml`.

## Steps

1. **Resolve identifiers if you only have addresses** — `mpxnFromAddress` (`GET /find-mpxn/{identifier}/{address}`) takes a UK post code and a partial address, both with `+` instead of spaces, partial address under 30 characters. It returns the most recently commissioned ESME at that address, falling back to the GSME. A `400 "The Request does not uniquely identify a Premises."` means you must narrow the address.
2. **Or verify a single MPxN first** — `RetrieveMPxNAvailability` (`GET /find-mpxn/{identifier}`).
3. **Submit the batch** — `ReadInventory` (`POST /read-inventory`) with a body of `mpxns`, `uprns` and/or `deviceIds` arrays. **Maximum 200 items per array.** Response is `{status, uuid, uri}` — a 200 means the job was accepted, not that the data is ready.
4. **Fetch the result from `uri`.** It is a CloudFront-hosted JSON file.
   - Simple requests: 1-10 seconds per MPxN.
   - With `last-communications=true` or `check-firmware=true`: the service goes out to the physical devices; allow **up to 1 hour**, after which the request times out and no file is ever written — resubmit.
   - `403 Access Denied` on the URI means no information is available (not an auth problem).
   - If collection failed, the **file content** is the error.
   - **Files are deleted after two days.** Persist what you need.
5. **Understand the cache.** Responses are cached. Only `last-communications` or `check-firmware` force a fresh device round-trip. Use them deliberately, not by default.

## Quotas — this operation is not retry-safe

- `429 "The list of element chosen in request (mpxn/uprn/deviceId) exceeds the maximum items allowed (200)."` — split the batch.
- `429 "Too many inputs on the request. You are still allowed to process ... valid inputs ..."` — you have hit the **1,000,000 processed-entries daily threshold**, summed across every element of every request that day.

Each submission consumes quota and mints a new `uuid`. **Never blind-retry a 429.** Retry with backoff only on 5xx. See `rate-limits/n3rgy-rate-limits.yml`.

## Sandbox

Use the `sandbox_read_inventory` fixtures in `sandbox/n3rgy-sandbox.yml` (e.g. MPxN `1100000000001`, UPRN `110000001`) — the consented-data MPxNs are a different fixture set and carry no UPRNs. **Do not set `check-firmware` or `last-communications` in the sandbox**; the guide states they will not work and return an error.

## Caveat the provider itself flags

Responses using `check-firmware` "might have mismatches" (change log 1.11). Treat firmware fields as advisory, not authoritative.

## Errors

- `400 "The request's body is empty."`
- `400 "There are no inputs on the request."` — body present but every array empty.

Full catalogue: `errors/n3rgy-problem-types.yml`.
