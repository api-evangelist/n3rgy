---
generated: '2026-07-27'
method: generated
name: Subscribe to push notifications instead of polling
description: >-
  Register an HTTPS endpoint and per-device-type subscriptions so n3rgy pushes
  when new readings land, then verify delivery — including what the contract does
  not give you.
api: openapi/n3rgy-customer-service-api-v2-openapi.yaml
operations: [GetPushNotificationConfiguration, EditPushNotificationConfiguration, DeletePushNotificationConfiguration, RetrievePushNotificationStatus]
source: >-
  Every operationId verified verbatim in
  openapi/n3rgy-customer-service-api-v2-openapi.yaml. Behaviour and warnings from
  the Push Notification section of
  https://customer-api-user-manuals.data.n3rgy.com/requests/.
---

# Subscribe to push notifications instead of polling

n3rgy will push to an endpoint you own when new readings arrive, rather than making you poll `RetrieveDataForReadingType`. The configuration is **one endpoint per account**, subscribed by device type and utility type.

## Auth

- `x-api-key` only — no consent check on any of the four push operations. See `authentication/n3rgy-authentication.yml`.

## Steps

1. **Read the current configuration** — `GetPushNotificationConfiguration` (`GET /push/configuration`). Returns `pushNotificationURL` and `deviceConfigurations`.
2. **Set the configuration** — `EditPushNotificationConfiguration` (`POST /push/configuration`). Success is **204 with no body**.
   ```json
   {
     "uri": "https://your-endpoint.example.com/n3rgy",
     "esme": ["IMPORT", "TARIFF"],
     "gsme": ["IMPORT"]
   }
   ```
   - `esme` accepts `IMPORT`, `EXPORT`, `TARIFF`. `gsme` accepts `IMPORT`, `TARIFF`.
3. **Verify delivery** — `RetrievePushNotificationStatus` (`GET /push/status`) returns `{lastHttpStatus, lastResponse, date}` from the most recent delivery attempt. This is your only delivery telemetry. `404 "No records for push notification status found at this time."` means nothing has been delivered yet.
4. **Tear down** — `DeletePushNotificationConfiguration` (`DELETE /push/configuration`).

## Replace semantics — read this before you PATCH-think

`POST /push/configuration` **replaces all existing configuration**. Specifically, from the guide:

- Sending an **empty body resets both** `esme` and `gsme`.
- Setting `esme` or `gsme` to an **empty list removes** those configurations.
- Setting `uri` to empty does **NOT** remove the registered endpoint.
- Values override existing configuration "even when empty".

So: always GET the current configuration, merge client-side, and POST the complete desired state. Never POST a partial body expecting a merge.

Partial validation applies to the lists: "If the entire body is invalid, an error is returned... If only a few entries are invalid, they are highlighted in the response and the process continues to the valid entries." Always re-GET after a POST to confirm what actually stuck.

## What the contract does not give you

- **No payload schema.** n3rgy publishes no description of the pushed message. Treat the payload as a *signal that something changed*, and re-fetch authoritative data with `RetrieveDataForReadingType`.
- **No signature or signing secret.** There is no way to verify the sender. Do not trust payload contents; consider IP allow-listing and a hard-to-guess path.
- **No retry, backoff or dead-letter policy** is documented.
- **One URI per account** — no per-property or per-MPxN routing. Fan out yourself from the payload.

See `asyncapi/n3rgy-push-notifications-webhooks.yml` for the full surface capture and gap list.

## Your endpoint should

- Accept `POST` over HTTPS and return 2xx fast — n3rgy records the status and body it saw and exposes them at `GET /push/status`.
- Be idempotent on its own side. n3rgy publishes no delivery-once guarantee and no event id.

## Errors

- `403 "User is not authorized to access this resource with an explicit deny."` on all four operations for an absent or invalid key.

Full catalogue: `errors/n3rgy-problem-types.yml`.
