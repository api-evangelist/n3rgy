# n3rgy

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
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
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

**Areas:** Energy · United Kingdom · Utilities · Smart Metering · Electricity · Gas · Smart Meter Data · Consent · Metering · Energy Data

## n3rgy on APIs.io

Everything profiled for n3rgy is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/n3rgy/](https://apis.io/providers/n3rgy/)** — or go straight to one of the APIs or properties below.

### APIs (13)

- [n3rgy Create Export Profiles API](https://apis.io/apis/n3rgy/n3rgy-create-export-profiles-api/) — The Create Export Profiles API from n3rgy — 1 operation(s) for create export profiles.
- [n3rgy Customer Service API V2 API](https://apis.io/apis/n3rgy/n3rgy-customer-service-api-v2-api/) — The Customer Service API V2 API from n3rgy — 1 operation(s) for customer service api v2.
- [n3rgy Find Mpxn API](https://apis.io/apis/n3rgy/n3rgy-find-mpxn-api/) — The Find Mpxn API from n3rgy — 2 operation(s) for find mpxn.
- [n3rgy Get Update Frequencies API](https://apis.io/apis/n3rgy/n3rgy-get-update-frequencies-api/) — The Get Update Frequencies API from n3rgy — 1 operation(s) for get update frequencies.
- [n3rgy Internal API](https://apis.io/apis/n3rgy/n3rgy-internal-api/) — The Internal API from n3rgy — 1 operation(s) for internal.
- [n3rgy Mpxn API](https://apis.io/apis/n3rgy/n3rgy-mpxn-api/) — The Mpxn API from n3rgy — 3 operation(s) for mpxn.
- [n3rgy Push API](https://apis.io/apis/n3rgy/n3rgy-push-api/) — The Push API from n3rgy — 2 operation(s) for push.
- [n3rgy Read Inventory API](https://apis.io/apis/n3rgy/n3rgy-read-inventory-api/) — The Read Inventory API from n3rgy — 1 operation(s) for read inventory.
- [n3rgy Reset All Update Frequencies API](https://apis.io/apis/n3rgy/n3rgy-reset-all-update-frequencies-api/) — The Reset All Update Frequencies API from n3rgy — 1 operation(s) for reset all update frequencies.
- [n3rgy Set Defaults API](https://apis.io/apis/n3rgy/n3rgy-set-defaults-api/) — The Set Defaults API from n3rgy — 1 operation(s) for set defaults.
- [n3rgy Set Meter Update Frequency API](https://apis.io/apis/n3rgy/n3rgy-set-meter-update-frequency-api/) — The Set Meter Update Frequency API from n3rgy — 1 operation(s) for set meter update frequency.
- [n3rgy Update Now API](https://apis.io/apis/n3rgy/n3rgy-update-now-api/) — The Update Now API from n3rgy — 1 operation(s) for update now.
- [n3rgy Upload API](https://apis.io/apis/n3rgy/n3rgy-upload-api/) — The Upload API from n3rgy — 4 operation(s) for upload.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [N3Rgy Push Notifications Webhooks](https://apis.io/asyncapis/n3rgy/n3rgy-push-notifications-webhooks/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [n3rgy](https://apis.io/servers/n3rgy/n3rgy/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [N3Rgy Agentic Access](https://apis.io/agentic-access/n3rgy/n3rgy-agentic-access/)

#### Examples (7)

Example requests and responses.

- [N3Rgy Error Bad Request Example](https://apis.io/examples/n3rgy/n3rgy-error-bad-request-example/)
- [N3Rgy Error Forbidden Example](https://apis.io/examples/n3rgy/n3rgy-error-forbidden-example/)
- [N3Rgy Push Configuration Request Example](https://apis.io/examples/n3rgy/n3rgy-push-configuration-request-example/)
- [N3Rgy Push Configuration Response Example](https://apis.io/examples/n3rgy/n3rgy-push-configuration-response-example/)
- [N3Rgy Push Status Response Example](https://apis.io/examples/n3rgy/n3rgy-push-status-response-example/)
- [N3Rgy Retrieve Consented Mpxns Empty Example](https://apis.io/examples/n3rgy/n3rgy-retrieve-consented-mpxns-empty-example/)
- [N3Rgy Retrieve Consented Mpxns Example](https://apis.io/examples/n3rgy/n3rgy-retrieve-consented-mpxns-example/)

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [N3Rgy Customer Service Api V2 Overlay](https://apis.io/overlays/n3rgy/n3rgy-customer-service-api-v2-overlay/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [N3Rgy Authentication](https://apis.io/security/n3rgy/n3rgy-authentication/)
- [N3Rgy Domain Security](https://apis.io/security/n3rgy/n3rgy-domain-security/)

#### Rate limits (1)

Published request limits.

- [N3Rgy Rate Limits](https://apis.io/rate-limits/n3rgy/n3rgy-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.n3rgy.com/)
- [Documentation](https://customer-api-user-manuals.data.n3rgy.com/)
- [Pricing](https://www.n3rgy.com/business/)
- [Sign up](https://data.n3rgy.com/business-sign-up)
- [Support](https://www.n3rgy.com/contact-us/)
- [Terms of service](https://www.n3rgy.com/wp-content/uploads/2023/04/N3rgyDataLimited.pdf)
- [Privacy policy](https://www.n3rgy.com/privacy/)
- [GitHub](https://github.com/n3rgy)

## API Evangelist rating

**Kin Score 47.0** — developing · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 66.1 |
| Contract quality | 59.4 |
| Contract governance | 4.5 |
| Operational transparency | 57.9 |
| Developer ergonomics | 35.1 |
| Access clarity | 38.2 |

**Agent readiness 35.2** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | verified |
| OpenAPI Examples | partial |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | yes |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | partial |
| Operation Distinctiveness | distinct |

**Regulatory alignment 36.9** — Energy & Utilities

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/n3rgy/](https://apis.io/providers/n3rgy/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for n3rgy: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/n3rgy/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
