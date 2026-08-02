---
name: Benchmark pay with Visier Compensation Benchmarks
description: Standardize a job title against the Visier taxonomy, resolve the benchmark dimensions, and retrieve market base-salary benchmarks singly or in bulk.
api: openapi/visier-compensation-benchmarks-openapi.yaml
operations:
  - GetInfo
  - GetJobsV2
  - SearchJobs
  - StandardizeJobsInBulk
  - GetJobHierarchies
  - GetLocations
  - SearchLocationsInBulk
  - GetIndustries
  - GetCompanySizes
  - GetCareerLevels
  - SearchCareerLevelsInBulk
  - GetSalaryBenchmark
  - GetSalaryBenchmarksInBulk
  - SubmitSalaryBenchmarkFeedback
  - GetTaxonomyChangeInfo
generated: '2026-08-02'
method: generated
source: openapi/visier-compensation-benchmarks-openapi.yaml
---

# Benchmark pay with Visier Compensation Benchmarks

This is a **dataset** API, separate from the tenant's own people data. It answers "what does the
market pay for this job, in this place, at this size and level". It authenticates with the `apikey`
header (`x-api-key` on some deployments — check `authentication/visier-authentication.yml`).

A benchmark is only meaningful once all of its dimensions are resolved to taxonomy values. Resolve
first; request the number last.

## 1. Resolve the job

Free-text job titles are not benchmark keys.

- `StandardizeJobsInBulk` (`POST /v1/compensation-benchmarks/jobs/standardize`) — map your titles to
  Visier taxonomy jobs. This is the right first call for a whole job architecture.
- `SearchJobs` (`POST /v1/compensation-benchmarks/jobs/search`) — interactive lookup.
- `GetJobsV2` (`GET /v2/compensation-benchmarks/jobs`) — browse the taxonomy. Prefer v2 over
  `GetJobsV1`.
- `GetJobHierarchies` (`GET /v1/compensation-benchmarks/jobs/hierarchies`) — the job family structure,
  for rolling results up.

## 2. Resolve the other dimensions

- `GetLocations` / `SearchLocationsInBulk` — geography.
- `GetIndustries` — industry.
- `GetCompanySizes` — headcount band.
- `GetCareerLevels` / `SearchCareerLevelsInBulk` — level.

## 3. Get the benchmark

- `GetSalaryBenchmark` (`GET /v1/compensation-benchmarks/base-salary`) — one benchmark.
- `GetSalaryBenchmarksInBulk` (`POST /v1/compensation-benchmarks/base-salaries`) — many. Use this
  rather than looping the single-record call; the rate limit is 100 calls/minute and a job
  architecture will exceed it in seconds.

Filter with `hasBenchmarkValue` when you only want combinations that actually have data.

## 4. Close the loop

- `SubmitSalaryBenchmarkFeedback` (`POST /v1/compensation-benchmarks/base-salary/feedback`) and
  `SubmitJobsFeedback` (`POST /v1/compensation-benchmarks/jobs/feedback`) — report a bad match or a
  suspect value.
- `GetInfo` (`GET /v1/compensation-benchmarks/info`) — dataset vintage. Include it whenever you
  present a number.
- `GetTaxonomyChangeInfo` (`GET /v1/compensation-benchmarks/taxonomy-change-info`) — check before a
  refresh; a taxonomy change can silently move your mappings.

## Rules

- **Never present a benchmark without its dimensions and its vintage.** "$X for this job" with no
  location, level, industry, size or as-of date is a misleading number.
- A missing benchmark is a real answer. Do not substitute the nearest job, widen the geography, or
  interpolate silently — say which combination had no data.
- Standardization is a *suggestion*. Review low-confidence job matches before pay decisions rest on
  them.
- Pay data drives compensation decisions with legal exposure. Keep the resolved dimensions and the
  dataset version alongside every stored benchmark so a decision can be audited.
- 206 means truncated; page with `start`/`limit`.

See `rate-limits/visier-rate-limits.yml` and `errors/visier-problem-types.yml`.
