---
name: Query workforce metrics from Visier
description: Discover the tenant's analytic model, then run an aggregate or list query against it and read the results correctly.
api: openapi/visier-data-out-apis-openapi.yaml
operations:
  - DataModel_AnalyticObjects
  - DataModel_Metrics
  - DataModel_Metric
  - DataModel_MetricDimensions
  - DataModel_Dimensions
  - DataModel_Members
  - DataQuery_Aggregate
  - DataQuery_List
  - Query_Snapshot
generated: '2026-08-02'
method: generated
source: openapi/visier-data-out-apis-openapi.yaml + openapi/visier-analytic-model-apis-openapi.yaml
---

# Query workforce metrics from Visier

Visier queries are **model-driven**. You cannot write a useful query without first discovering what
the tenant's model contains — metric ids and dimension ids differ per tenant. Discover first, then
query. Never invent a metric id.

## 1. Authenticate

Follow `visier-authenticate.md`. `read` scope is enough for everything in this skill.

## 2. Discover the model

- `DataModel_AnalyticObjects` (`GET /v1/data/model/analytic-objects`) — what subjects exist
  (employees, applicants, requisitions, and so on).
- `DataModel_Metrics` (`GET /v1/data/model/metrics`) — what is measurable. Use `DataModel_Metric`
  (`GET /v1/data/model/metrics/{id}`) for one metric's definition.
- `DataModel_MetricDimensions` (`GET /v1/data/model/metrics/{metricId}/dimensions`) — the legal ways
  to slice that metric. Slicing by a dimension that is not on this list will fail.
- `DataModel_Dimensions` (`GET /v1/data/model/analytic-objects/{objectId}/dimensions`) — dimensions
  on an object.
- `DataModel_Members` (`GET /v1/data/model/analytic-objects/{objectId}/dimensions/{dimensionId}/members`)
  — the concrete values to filter on.

Cache the discovery results for the session; do not re-walk the model for every query.

## 3. Run the query

- `DataQuery_Aggregate` (`POST /v1/data/query/aggregate`) — the default. Returns a metric aggregated
  over a time interval and sliced by the axes you name.
- `DataQuery_List` (`POST /v1/data/query/list`) — row-level detail. Use only when the caller
  genuinely needs individual records; it returns people data.
- `Query_Snapshot` (`POST /v1/data/query/snapshot`) — point-in-time state.

Send `TargetTenantID` when the credential spans more than one tenant.

## 4. Read the response honestly

- **HTTP 206 means the result was truncated** by the `limit` parameter. Say so in the answer, or
  page with `start`/`limit` until complete. Reporting a truncated aggregate as the total is wrong.
- Results reflect the **latest published data version**, not live HRIS state. If recency matters,
  check the data version with `DataAndJobHandling_LatestEnabledDV`.
- If a currency-converted measure looks off, note that `currencyConversionMode` on the query
  execution options is deprecated in the published spec.

## Rules

- Rate limits are 100/minute and 6000/hour. Read `X-RateLimit-Remaining-Minute` on every response and
  slow down before you hit 429 — batch axes into one aggregate query instead of looping one query
  per slice.
- There is no idempotency key. Queries are reads and safe to retry; retry on 500/502/504 with
  backoff, but never blind-retry a 400.
- On an error, surface the `rci` value — that is the identifier Visier support traces.
- List queries return personal data. Do not persist, echo, or forward employee-level rows beyond what
  the caller asked for.

See `conventions/visier-conventions.yml`, `rate-limits/visier-rate-limits.yml`,
`errors/visier-problem-types.yml`, and `data-model/visier-data-model.yml`.
