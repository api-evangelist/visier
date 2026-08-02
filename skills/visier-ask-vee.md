---
name: Ask Vee a natural-language workforce question
description: Use Visier's Vee agent to answer a workforce question in natural language, via the REST API or the hosted Query MCP server, and fall back to structured queries when Vee cannot answer.
api: openapi/visier-data-out-apis-openapi.yaml
operations:
  - VeeV1_VeeStatus
  - VeeV1_VeeSampleQuestions
  - VeeV1_VeeSampleQuestionCategories
  - VeeV1_VeeQuestionRequest
  - VeeV1_VeeFeedback
generated: '2026-08-02'
method: generated
source: openapi/visier-data-out-apis-openapi.yaml + https://docs.visier.com/developer/apis/data-out/vee/vee-api.htm
---

# Ask Vee a natural-language workforce question

Vee is Visier's purpose-built workforce analytics agent. It interprets the question, decides how to
query the tenant's data, and answers in natural language. Prefer Vee over hand-built queries for
ordinary questions — Visier tunes it against the common workforce analytics question set.

## Two surfaces, same agent

- **REST**: `VeeV1_VeeQuestionRequest` (`POST /v1/vee/question`) on
  `https://{vanity_name}.api.visier.io`.
- **MCP**: the "Ask Vee AI agent" tool on
  `https://{vanity_name}.app.visier.com/visier-query-mcp` (OAuth 2.0, HTTPS/SSE).

Use MCP when you are already an MCP client; use REST when you are building an application.

## Steps

1. Authenticate — see `visier-authenticate.md`. Vee requires the **Vee Core** capability on the user.
2. Check availability with `VeeV1_VeeStatus` (`GET /v1/vee/status`) before a first call in a session.
3. If the caller is unsure what to ask, offer real options rather than guessing: pull
   `VeeV1_VeeSampleQuestionCategories` (`GET /v1/vee/sample-question-categories`) and
   `VeeV1_VeeSampleQuestions` (`GET /v1/vee/sample-questions`).
4. Ask the question with `VeeV1_VeeQuestionRequest`. Send `TargetTenantID` when the credential spans
   multiple tenants.
5. Send the answer's quality back with `VeeV1_VeeFeedback` (`POST /v1/vee/feedback`) when the user
   rates it. This is how the agent improves; do not skip it in interactive integrations.

## When Vee cannot answer

Fall through to the structured path in `visier-query-workforce-metrics.md`: discover the model with
`DataModel_Metrics` / `DataModel_MetricDimensions`, then run `DataQuery_Aggregate`. Do this when:

- Vee returns no answer or an explicit inability,
- the user wants to see the reasoning rather than a summary,
- or the question needs several chained queries.

## Rules

- Vee's answer reflects the tenant's data **as of the latest data load**. Do not present it as live.
- Vee inherits the calling user's permissions and data access. Never use an impersonation token to
  widen what a question can see.
- Vee calls count against the same rate limits (100/minute, 6000/hour).
- Answers concern real employees. Do not persist or forward Vee output beyond the requesting user's
  session without an explicit instruction to.
- Do not paraphrase a Vee number into a stronger claim than it made — if Vee qualified the answer,
  carry the qualification through.

See `mcp/visier-mcp.yml` and `mcp/visier-tool-crosswalk.yml`.
