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

Visier is a workforce and people analytics platform that consolidates HR, talent, compensation, and operational data into a purpose-built people data model, then exposes that model for analysis, planning, and AI-assisted question answering. Visier publishes a broad suite of public REST APIs — Data In (Direct Data Intake, Data Upload, job handling), Data Out (Data Query, Vee, exports), Administration (tenants, users, profiles, permissions, projects), Analytic Model (data model, concepts, metrics, dimensions), Planning, Webhooks, and dataset APIs such as Compensation Benchmarks and the Skills Intelligence Engine. OpenAPI v3 definitions for every collection are published on GitHub at visier/openapi-clients, generated Python SDKs ship to PyPI, and a hosted Visier Query MCP server exposes Vee and data-query tools to MCP clients over OAuth 2.0.

**Areas:** Company · People Analytics · Workforce Analytics · Human Resources · HR Technology · Workforce Planning · Analytics · Business Intelligence · Compensation · Skills · Artificial Intelligence · MCP

## Visier on APIs.io

Everything profiled for Visier is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/visier/](https://apis.io/providers/visier/)** — or go straight to one of the APIs or properties below.

### APIs (51)

- [Visier Query MCP Server](https://apis.io/apis/visier/query-mcp/) — Visier's hosted Model Context Protocol server, exposing Vee (natural-language workforce question answering) and structured data-query tools to MCP clients…
- [Visier Analytic Objects V2 API](https://apis.io/apis/visier/visier-analyticobjectsv2-api/) — Create, retrieve, update, and delete analytic objects in your analytic model. You can create, update, and delete one or more analytic objects in an API…
- [Visier Benchmarks API](https://apis.io/apis/visier/visier-benchmarks-api/) — Get benchmark values.
- [Visier Concepts V2 API](https://apis.io/apis/visier/visier-conceptsv2-api/) — Create, retrieve, update, and delete concepts in your analytic model. You can create, update, and delete one or more concepts in an API call.
- [Visier Consolidated Analytics API](https://apis.io/apis/visier/visier-consolidatedanalytics-api/) — Manage your consolidated analytics (CA) tenants in Visier, such as retrieving the details of CA tenants, creating CA tenants, adding or deleting source…
- [Visier Data And Job Handling API](https://apis.io/apis/visier/visier-dataandjobhandling-api/) — Initiate and manage jobs, included or excluded data, and data connector credentials. Administrating tenant users can manage jobs and data for their analytic…
- [Visier Data Export Connectors API](https://apis.io/apis/visier/visier-dataexportconnectorsapi-api/) — Manage data export connectors and credentials, and run data export connector jobs. Data export connectors send Visier data to external systems, such as…
- [Visier Data Intake API](https://apis.io/apis/visier/visier-dataintake-api/) — Send raw or untransformed data to Visier. After we receive the data, Visier runs business rules to transform your data into the expected format for the…
- [Visier Data Version Export API](https://apis.io/apis/visier/visier-dataversionexport-api/) — Export Visier data version information, such as tables, columns, and file information, in CSV format. <br>**Note:** <em>This API is in **alpha**. While in…
- [Visier Dimensions API](https://apis.io/apis/visier/visier-dimensions-api/) — Discover dimensions and members. A dimension organizes unique values of an attribute into a list or a hierarchical structure of members. The structure can…
- [Visier Dimensions V2 API](https://apis.io/apis/visier/visier-dimensionsv2-api/) — Create, retrieve, update, and delete dimensions in your analytic model. You can create, update, and delete one or more dimensions in an API call.…
- [Visier Direct Data Intake API](https://apis.io/apis/visier/visier-directdataintake-api/) — Use the Direct Data Intake API to load data directly into Visier objects. These objects can be delivered as part of Visier Blueprint, locally modified…
- [Visier Email Domains API](https://apis.io/apis/visier/visier-emaildomains-api/) — Manage the list of user email address domains that are allowed in your tenant. <br>**Note:** <em>This API is in **alpha**. While in alpha, APIs may change…
- [Visier Jobs Library API](https://apis.io/apis/visier/visier-jobs-library-api/) — Access over 3,300 standard jobs and get complete details in 27 languages, such as alternative titles, descriptions, and skills.
- [Visier Metrics V2 API](https://apis.io/apis/visier/visier-metricsv2-api/) — Create, retrieve, update, and delete simple and derived metrics in your analytic model. A simple metric is a metric based on one or more analytic objects. A…
- [Visier Object Configuration API](https://apis.io/apis/visier/visier-objectconfiguration-api/) — Manage objects in your analytic model.
- [Visier Permissions API](https://apis.io/apis/visier/visier-permissions-api/) — Manage permissions in Visier, such as retrieving the details of a permission, content package, or data access set, creating new permissions and data access…
- [Visier Personalized Alerts API](https://apis.io/apis/visier/visier-personalizedalerts-api/) — Manage your personalized alerts in Visier. Alerts notify you if a metric exceeds your defined threshold. <br>**Note:** <em>This API is in **alpha**. While…
- [Visier PGP Keys API](https://apis.io/apis/visier/visier-pgpkeys-api/) — The Pretty Good Privacy (PGP) Keys API generates key pairs and provides a public key to encrypt data that you send to Visier. PGP encryption adds an…
- [Visier Plan Administration API](https://apis.io/apis/visier/visier-planadministration-api/) — Manage collaboration projects in your plans, including actions such as consolidating and reopening subplans.
- [Visier Plan Data Load API](https://apis.io/apis/visier/visier-plandataload-api/) — Send data directly to your plan's scenario and optionally add or remove rows from your plan.
- [Visier Plan Events API](https://apis.io/apis/visier/visier-planevents-api/) — Retrieve details about planning events such as member promotions and row changes.
- [Visier Production Versions API](https://apis.io/apis/visier/visier-productionversions-api/) — Use this API to retrieve information about data versions that were published to production. In Visier, production is the version of Visier available to your…
- [Visier Profiles API](https://apis.io/apis/visier/visier-profiles-api/) — Manage the profiles assigned to users, such as assigning or removing a profile from a list of users and retrieving profile details. Administrating tenant…
- [Visier Projects API](https://apis.io/apis/visier/visier-projects-api/) — Create projects, publish projects, and retrieve project details.
- [Visier Release Version Configuration API](https://apis.io/apis/visier/visier-releaseversionconfiguration-api/) — Manage the Visier product release versions for your tenants. <br>**Note:** <em>This API is available for Embedded Partners.</em> <br>**Note:** <em>This API…
- [Visier Reporting API](https://apis.io/apis/visier/visier-reporting-api/) — Create, retrieve, delete, copy, and download reports. <br>**Note**: This API is available for Embedded Partners. <br>**Note:** <em>This API is in **alpha**.…
- [Visier Search API](https://apis.io/apis/visier/visier-search-api/) — Search for documents, such as analyses, in Visier. <br>**Note:** <em>This API is in **alpha**. While in alpha, APIs may change in a breaking way without…
- [Visier Sidecar Solutions API](https://apis.io/apis/visier/visier-sidecarsolutions-api/) — Manage your sidecar solution's configuration. A sidecar solution is a unique solution built using the Visier platform, such as Smart Compensation. Use this…
- [Visier Skills Library API](https://apis.io/apis/visier/visier-skills-library-api/) — Access over 14,000 skills and get complete skill details in 27 languages, such as alternative titles, descriptions, and hierarchies.
- [Visier Source Files Download API](https://apis.io/apis/visier/visier-sourcefilesdownload-api/) — Download a tenants source files. <br>**Note:** <em>This API is in **alpha**. While in alpha, APIs may change in a breaking way without notice; functionality…
- [Visier Sources API](https://apis.io/apis/visier/visier-sources-api/) — Export and import sources in Visier. <br>**Note:** <em>This API is in **beta**. While in beta, APIs are interface-stable and implementation may change…
- [Visier Table Source API](https://apis.io/apis/visier/visier-tablesource-api/) — Use row-based management for your source data in Visier. The Table Source API supports direct SQL-based data modifications, eliminating concerns about file…
- [Visier Tenants V1 API](https://apis.io/apis/visier/visier-tenantsv1-api/) — Create analytic tenants, retrieve tenant information, and validate metric values.
- [Visier Tenants V2 API](https://apis.io/apis/visier/visier-tenantsv2-api/) — Create analytic tenants, deprovision tenants, retrieve tenant information, and update tenant information. Tenants V2 improves upon Tenants V1 in the…
- [Visier Vee Configuration API](https://apis.io/apis/visier/visier-veeconfiguration-api/) — Manage Vee v2 instructions and safeguards for a tenant. Instructions guide Vee's behavior when responding to queries. Safeguards prevent Vee from responding…
- [Visier Vee V1 API](https://apis.io/apis/visier/visier-veev1-api/) — Use Vee through Visier APIs, such as asking questions, submitting feedback, and getting sample questions.
- [Visier Vee V2 API](https://apis.io/apis/visier/visier-veev2-api/) — Use Vee through Visier APIs, such as getting sample questions. Vee V2 improves upon Vee V1 by aligning response field names with the Vee UI.
- [Visier Webhooks API](https://apis.io/apis/visier/visier-webhooks-api/) — Create, manage, and retrieve webhook definitions. Use webhooks to register your own HTTPS endpoints with Visier and listen for specific events. When these…
- [Visier O Auth2 API](https://apis.io/apis/visier/visier-oauth2-api/) — Request an authentication token through OAuth 2.0 with Open ID Connect (OIDC). With OAuth 2.0 with OIDC, use an OAuth 2.0 grant to request an authentication…
- [Visier Basic Authentication API](https://apis.io/apis/visier/visier-basic-authentication-api/) — Request an authentication token through basic authentication. With basic authentication, use your username and password to request a secure token. The…
- [Visier Data Model API](https://apis.io/apis/visier/visier-data-model-api/) — Discover the objects that make up your Visier solution and provide detailed information on the object's schema. You can retrieve detailed information about…
- [Visier Data Query API](https://apis.io/apis/visier/visier-data-query-api/) — Query against your data in Visier to get aggregate and list data.
- [Visier Data Upload API](https://apis.io/apis/visier/visier-data-upload-api/) — Send data files to Visier. After we receive the data, Visier starts a receiving job and a processing job to process the data.
- [Visier Encryption Keys API](https://apis.io/apis/visier/visier-encryption-keys-api/) — Manage the encryption keys in your Visier tenant. Administrating tenants can specify the tenant in which to manage keys using the `TargetTenantID` header.…
- [Visier Network Subnets API](https://apis.io/apis/visier/visier-network-subnets-api/) — Manage the IP addresses that can call Visier APIs. **Note:** This API is in **alpha**. While in alpha, APIs may change in a breaking way without notice;…
- [Visier System Status API](https://apis.io/apis/visier/visier-system-status-api/) — Check the health and status of Visier's platform and services.
- [Visier User Groups V2 API](https://apis.io/apis/visier/visier-user-groups-v2-api/) — Manage user groups in Visier, such as creating, updating, and deleting user groups in bulk.
- [Visier Users V1 API](https://apis.io/apis/visier/visier-users-v1-api/) — Manage users within an organization, such as assigning permissions to users and retrieving user permission assignments and application logs. **Tip:** Visier…
- [Visier Users V2 API](https://apis.io/apis/visier/visier-users-v2-api/) — Manage users in bulk, such as creating, updating, and deleting many users. **Tip:** Visier recommends that administrating tenant users focus primarily on…
- [Visier Users V3 API](https://apis.io/apis/visier/visier-users-v3-api/) — Manage users within an organization. Users V3 offers the ability to update or insert (upsert) a user.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Visier Webhooks](https://apis.io/asyncapis/visier/visier-webhooks/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [Visier Query MCP Server](https://apis.io/servers/visier/visier-query-mcp-server/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Visier Agentic Access](https://apis.io/agentic-access/visier/visier-agentic-access/)

#### Collections (50)

Postman and Open Collection request collections.

- [Visier Analytic Model Analytic Objects V2 API](https://apis.io/collections/visier/open-visier-analyticobjectsv2-api/)
- [Visier Authentication Basic Authentication API](https://apis.io/collections/visier/open-visier-basicauthentication-api/)
- [Compensation Benchmarks API](https://apis.io/collections/visier/open-visier-benchmarks-api/)
- [Visier Analytic Model Concepts V2 API](https://apis.io/collections/visier/open-visier-conceptsv2-api/)
- [Visier Administration Consolidated Analytics API](https://apis.io/collections/visier/open-visier-consolidatedanalytics-api/)
- [Visier Data In Data And Job Handling API](https://apis.io/collections/visier/open-visier-dataandjobhandling-api/)
- [Visier Data Out Data Export Connectors API API](https://apis.io/collections/visier/open-visier-dataexportconnectorsapi-api/)
- [Visier Data In Data Intake API](https://apis.io/collections/visier/open-visier-dataintake-api/)
- [Visier Analytic Model Data Model API](https://apis.io/collections/visier/open-visier-datamodel-api/)
- [Visier Data Out Data Query API](https://apis.io/collections/visier/open-visier-dataquery-api/)
- [Visier Data In Data Upload API](https://apis.io/collections/visier/open-visier-dataupload-api/)
- [Visier Data Out Data Version Export API](https://apis.io/collections/visier/open-visier-dataversionexport-api/)
- [Compensation Benchmarks Dimensions API](https://apis.io/collections/visier/open-visier-dimensions-api/)
- [Visier Analytic Model Dimensions V2 API](https://apis.io/collections/visier/open-visier-dimensionsv2-api/)
- [Visier Data In Direct Data Intake API](https://apis.io/collections/visier/open-visier-directdataintake-api/)
- [Visier Administration Email Domains API](https://apis.io/collections/visier/open-visier-emaildomains-api/)
- [Visier Administration Encryption Keys API](https://apis.io/collections/visier/open-visier-encryptionkeys-api/)
- [Skills Intelligence Engine Jobs Library API](https://apis.io/collections/visier/open-visier-jobs-library-api/)
- [Visier Analytic Model Metrics V2 API](https://apis.io/collections/visier/open-visier-metricsv2-api/)
- [Visier Administration Network Subnets API](https://apis.io/collections/visier/open-visier-networksubnets-api/)
- [Visier Authentication O Auth2 API](https://apis.io/collections/visier/open-visier-oauth2-api/)
- [Visier Analytic Model Object Configuration API](https://apis.io/collections/visier/open-visier-objectconfiguration-api/)
- [Visier Administration Permissions API](https://apis.io/collections/visier/open-visier-permissions-api/)
- [Visier Analytic Model Personalized Alerts API](https://apis.io/collections/visier/open-visier-personalizedalerts-api/)
- [Visier Data In PGP Keys API](https://apis.io/collections/visier/open-visier-pgpkeys-api/)
- …and 25 more published on APIs.io

#### Overlays (9)

OpenAPI overlays, including conversational phrasing for each operation.

- [Visier Administration Apis Overlay](https://apis.io/overlays/visier/visier-administration-apis-overlay/)
- [Visier Analytic Model Apis Overlay](https://apis.io/overlays/visier/visier-analytic-model-apis-overlay/)
- [Visier Authentication Apis Overlay](https://apis.io/overlays/visier/visier-authentication-apis-overlay/)
- [Visier Compensation Benchmarks Overlay](https://apis.io/overlays/visier/visier-compensation-benchmarks-overlay/)
- [Visier Data In Apis Overlay](https://apis.io/overlays/visier/visier-data-in-apis-overlay/)
- [Visier Data Out Apis Overlay](https://apis.io/overlays/visier/visier-data-out-apis-overlay/)
- [Visier Planning Overlay](https://apis.io/overlays/visier/visier-planning-overlay/)
- [Visier Skills Intelligence Engine Overlay](https://apis.io/overlays/visier/visier-skills-intelligence-engine-overlay/)
- [Visier Webhooks Overlay](https://apis.io/overlays/visier/visier-webhooks-overlay/)

#### Security (4)

Authentication, trust centre, and vulnerability disclosure.

- [Visier Authentication](https://apis.io/security/visier/visier-authentication/)
- [Visier Domain Security](https://apis.io/security/visier/visier-domain-security/)
- [Visier Trust Center](https://apis.io/security/visier/visier-trust-center/)
- [Visier Vulnerability Disclosure](https://apis.io/security/visier/visier-vulnerability-disclosure/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Visier Scopes](https://apis.io/scopes/visier/visier-scopes/)

#### Rate limits (1)

Published request limits.

- [Visier Rate Limits](https://apis.io/rate-limits/visier/visier-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.visier.com/)
- [Documentation](https://docs.visier.com/developer/Default.htm)
- [Getting started](https://docs.visier.com/developer/apis/apis-get-started-home.htm)
- [API reference](https://docs.visier.com/developer/apis/apis.htm)
- [Sign up](https://www.visier.com/login/)
- [Support](https://my.visier.com/csm?id=community_home)
- [Blog](https://www.visier.com/blog/)
- [Security](https://www.visier.com/.well-known/security.txt)
- [Compliance](https://www.visier.com/trust/compliance/)
- [Terms of service](https://www.visier.com/terms-of-use-agreement/)
- [Privacy policy](https://www.visier.com/privacy/)
- [GitHub](https://github.com/visier)
- [Status](https://status.visier.com/)

## API Evangelist rating

**Kin Score 65.0** — strong · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 78.6 |
| Contract quality | 51.7 |
| Contract governance | 4.5 |
| Operational transparency | 76.3 |
| Developer ergonomics | 82.7 |
| Access clarity | 50.0 |

**Agent readiness 37.2** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | documented (partial credit) |
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
| Delegated Identity | documented (partial credit) |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | — |
| Operation Distinctiveness | distinct |

**Regulatory alignment 49.1** — Employment & Payroll

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/visier/](https://apis.io/providers/visier/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Visier: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/visier/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
