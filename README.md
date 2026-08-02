# Visier

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
