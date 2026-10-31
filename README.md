# Samaya AI

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

Samaya AI builds domain-trained "Expert AI Agents" for financial services — investment research, client advisory and deal diligence — deployed across 10,000+ seats at bulge-bracket banks including Morgan Stanley. The platform ingests filings, broker research and a firm's own proprietary documents, reconciles figures across them, and cites every number it returns. Founded in 2022 by Maithra Raghu (formerly Google Brain) and Fabio Petroni, it raised a $43.5M Series A led by NEA with NVentures (NVIDIA), Databricks Ventures, Eric Schmidt and Yann LeCun participating. Its machine surface is agent-first: a live OAuth-protected remote MCP server at mcp.samaya.ai that connects ChatGPT, Claude and other AI applications to Samaya's research capabilities, plus a small "Samaya Public API" for org/team/user provisioning and an authenticated GraphQL endpoint behind the app.

**Areas:** Artificial Intelligence · Financial Services · Investment Research · AI Agents · MCP · Agent-Native · Capital Markets · Enterprise Search · Retrieval · GraphQL

## Samaya AI on APIs.io

Everything profiled for Samaya AI is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/samaya-ai/](https://apis.io/providers/samaya-ai/)** — or go straight to one of the APIs or properties below.

### APIs (5)

- [Samaya MCP Server](https://apis.io/apis/samaya-ai/samaya-mcp-server/) — Hosted remote MCP server at https://mcp.samaya.ai/mcp that connects ChatGPT, Claude and other AI applications to Samaya's expert financial research…
- [Samaya GraphQL API](https://apis.io/apis/samaya-ai/samaya-graphql-api/) — Application GraphQL endpoint at https://api.samaya.ai/graphql/ serving the Samaya web app at app.samaya.ai. The API host root 302s to /graphql/, and an…
- [Samaya AI Organizations API](https://apis.io/apis/samaya-ai/samaya-ai-organizations-api/) — The Organizations API from Samaya AI — 1 operation(s) for organizations.
- [Samaya AI Teams API](https://apis.io/apis/samaya-ai/samaya-ai-teams-api/) — The Teams API from Samaya AI — 2 operation(s) for teams.
- [Samaya AI Users API](https://apis.io/apis/samaya-ai/samaya-ai-users-api/) — The Users API from Samaya AI — 1 operation(s) for users.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [Samaya MCP Server](https://apis.io/servers/samaya-ai/samaya-mcp-server/)

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [Samaya Ai Public Api Overlay](https://apis.io/overlays/samaya-ai/samaya-ai-public-api-overlay/)

#### Security (3)

Authentication, trust centre, and vulnerability disclosure.

- [Samaya Ai Authentication](https://apis.io/security/samaya-ai/samaya-ai-authentication/)
- [Samaya Ai Domain Security](https://apis.io/security/samaya-ai/samaya-ai-domain-security/)
- [Samaya Ai Trust Center](https://apis.io/security/samaya-ai/samaya-ai-trust-center/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Samaya Ai Scopes](https://apis.io/scopes/samaya-ai/samaya-ai-scopes/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Samaya Ai Plans Pricing](https://apis.io/plans/samaya-ai/samaya-ai-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Samaya Ai Rate Limits](https://apis.io/rate-limits/samaya-ai/samaya-ai-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://samaya.ai/)
- [API reference](https://api.samaya.ai/v1/openapi.json)
- [Sign up](https://app.samaya.ai/sign-in)
- [Blog](https://samaya.ai/blog)
- [Compliance](https://trust.samaya.ai/)
- [Trust centre](https://trust.samaya.ai/)
- [Privacy policy](https://samaya.ai/privacy/privacy)
- [GitHub](https://github.com/samaya-ai)
- [Status](https://status.samaya.ai/)

## API Evangelist rating

**Kin Score 35.1** — thin · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 75.0 |
| Contract quality | 41.0 |
| Contract governance | 18.2 |
| Operational transparency | 18.4 |
| Developer ergonomics | 28.0 |
| Access clarity | 26.3 |

**Agent readiness 44.6** — agent-ready (gated down from agent-native)

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | — |
| Reversibility Documented | — |
| MCP Server | documented (partial credit) |
| Auth Clarity | served (partial credit) |
| Idempotency | — |
| Error Semantics | documented (partial credit) |
| OpenAPI Examples | — |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | — |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | served (partial credit) |
| Protected Resource Metadata | verified |
| Dynamic Client Registration | yes |
| Agentic Commerce | — |
| Pagination Ratio | paginated |
| Operation Distinctiveness | distinct |

**Regulatory alignment 32.7** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/samaya-ai/](https://apis.io/providers/samaya-ai/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Samaya AI: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/samaya-ai/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
