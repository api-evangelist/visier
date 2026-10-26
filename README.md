# Visier

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

Visier is a workforce and people analytics platform that consolidates HR, talent, compensation and
operational data into a purpose-built people data model, then exposes that model for analysis,
planning and AI-assisted question answering.

- Website: https://www.visier.com/
- Developer portal: https://www.visier.com/developer/
- Documentation: https://docs.visier.com/developer/Default.htm
- API reference: https://docs.visier.com/developer/apis/apis.htm
- GitHub: https://github.com/visier

## APIs

Visier publishes OpenAPI v3 definitions for every public API collection at
[visier/openapi-clients](https://github.com/visier/openapi-clients). Nine documents are harvested
here — 366 operations, 901 component schemas.

| Collection | Operations | Spec |
|---|---|---|
| Administration | 125 | `openapi/visier-administration-apis-openapi.yaml` |
| Analytic Model | 87 | `openapi/visier-analytic-model-apis-openapi.yaml` |
| Data In | 66 | `openapi/visier-data-in-apis-openapi.yaml` |
| Data Out | 38 | `openapi/visier-data-out-apis-openapi.yaml` |
| Compensation Benchmarks | 17 | `openapi/visier-compensation-benchmarks-openapi.yaml` |
| Skills Intelligence Engine | 13 | `openapi/visier-skills-intelligence-engine-openapi.yaml` |
| Webhooks (Beta) | 9 | `openapi/visier-webhooks-openapi.yaml` |
| Planning | 6 | `openapi/visier-planning-openapi.yaml` |
| Authentication | 5 | `openapi/visier-authentication-apis-openapi.yaml` |

API hosts are tenant-scoped: `https://{vanity_name}.api.visier.io`.

## Agents

Visier ships a hosted Model Context Protocol server —
`https://{vanity_name}.app.visier.com/visier-query-mcp` — exposing Vee (natural-language workforce
question answering) plus nine structured data-query tools over HTTPS/SSE with OAuth 2.0. See
`mcp/visier-mcp.yml` and the REST binding in `mcp/visier-tool-crosswalk.yml`.

## Artifacts

`openapi/` · `overlays/` · `mcp/` · `asyncapi/` (webhook event catalog) · `skills/` ·
`agentic-access/` · `authentication/` · `scopes/` · `conventions/` · `errors/` · `lifecycle/` ·
`changelog/` · `rate-limits/` · `conformance/` · `data-model/` · `packages/` · `cli/` ·
`components/` · `sandbox/` · `security/` · `well-known/` · `llms/`

No A2A agent card is published at `/.well-known/agent-card.json` or `/.well-known/agent.json`, so
no `a2a/` artifact exists — that one is search-only and never authored on a provider's behalf.
