# n3rgy (n3rgy)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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
