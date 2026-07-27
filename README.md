# n3rgy (n3rgy)

n3rgy data limited is a United Kingdom smart-energy data platform, registered in England (No. 11712674) and owned by Smart Metering Systems Ltd. It sits between Great Britain's mandated smart-metering infrastructure — the DCC network, SMETS2 home area networks (HANs), and the ESME/GSME electricity and gas meters behind them — and the organisations that want to read from it, letting a business collect consumption, production, and tariff data for a property (addressed by MPAN/MPRN, collectively MPxN) once the occupant has granted consent, without that business having to become a DCC user in its own right. Its API posture is public in documentation and closed in access: a genuinely anonymous MkDocs developer guide and a complete OpenAPI 3.0.1 contract for the Customer Service API V2 are served to anyone, while every operation is x-api-key gated and live keys must be enabled by the n3rgy back office after a business sign-up. Britain mandated the metering infrastructure, not a consumer data right, so nothing here is a Consumer Data Right or Green Button implementation — n3rgy publishes no open grid or market data at all, and the formerly public consumer API is, by the company's own statement, no longer available.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/n3rgy/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/n3rgy/refs/heads/main/apis.yml)

## Tags

- Energy
- United Kingdom
- Utilities
- Smart Metering
- Electricity
- Gas
- Smart Meter Data
- Consent
- Metering
- Energy Data

## Timestamps

- **Created:** 2026-07-27
- **Modified:** 2026-07-27

## APIs

### n3rgy Customer Service API V2

The consent-scoped smart-meter data API of the n3rgy platform. A business holding a valid n3rgy API key lists the properties (MPxNs) it has active consent for, discovers which utilities (electricity, gas) and reading types (consumption, production, tariff) are available for each, and retrieves the underlying half-hourly data. The same contract also covers meter update-frequency control, MPxN and address lookup, read-inventory / firmware and last-communications checks, on-demand "update now" fetches, push-notification configuration, and an upload/devices surface for non-DCC device data. Every operation is secured with the x-api-key header; consent-bearing operations additionally validate that an active consent exists for the HAN behind the given MPxN. A free sandbox with demonstration MPxNs mirrors the live contract on a separate host.

- **Human URL:** [https://customer-api-user-manuals.data.n3rgy.com/](https://customer-api-user-manuals.data.n3rgy.com/)
- **Base URL:** `https://api-v2.data.n3rgy.com`
- **Sandbox Base URL:** `https://api-v2-sandbox.data.n3rgy.com`

#### Tags

- Smart Metering
- Consumption
- Tariff
- Consent
- Electricity
- Gas

#### Properties

- [OpenAPI](openapi/n3rgy-customer-service-api-v2-openapi.yaml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://customer-api-user-manuals.data.n3rgy.com/)
- [API Reference](https://customer-api-user-manuals.data.n3rgy.com/api-specification/)
- [Authentication](https://customer-api-user-manuals.data.n3rgy.com/authentication/)
- [Requests](https://customer-api-user-manuals.data.n3rgy.com/requests/)
- [Schemas](https://customer-api-user-manuals.data.n3rgy.com/schemas/)
- [Sandbox](https://customer-api-user-manuals.data.n3rgy.com/sandbox-requests/)
- [Electricity Data Items](https://customer-api-user-manuals.data.n3rgy.com/electricity-format/)
- [Gas Data Items](https://customer-api-user-manuals.data.n3rgy.com/gas-format/)
- [Change Log](https://customer-api-user-manuals.data.n3rgy.com/change-log/)
- [Sign Up](https://data.n3rgy.com/business-sign-up)

## Common Properties

- [Website](https://www.n3rgy.com/)
- [Documentation](https://customer-api-user-manuals.data.n3rgy.com/)
- [Sign Up](https://data.n3rgy.com/business-sign-up)
- [Login](https://www.n3rgy.com/business-login/)
- [Consumer Portal](https://data.n3rgy.com/consumer-login)
- [Pricing](https://www.n3rgy.com/business/)
- [Terms of Service](https://www.n3rgy.com/wp-content/uploads/2023/04/N3rgyDataLimited.pdf)
- [Privacy Policy](https://www.n3rgy.com/privacy/)
- [Support](https://www.n3rgy.com/contact-us/)
- [About](https://www.n3rgy.com/about-us/)
- [GitHub Organization](https://github.com/n3rgy)

## Maintainers

- Kin Lane — kin@apievangelist.com
