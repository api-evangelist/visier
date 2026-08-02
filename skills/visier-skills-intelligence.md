---
name: Extract and match skills with the Visier Skills Intelligence Engine
description: Standardize job titles, extract skills from free text, and match skills to jobs against the Visier skills taxonomy.
api: openapi/visier-skills-intelligence-engine-openapi.yaml
operations:
  - ListSkills
  - GetSkill
  - SearchSkill
  - ExtractSkills
  - MatchSkills
  - ListSkillGroups
  - GetSkillGroup
  - ListSkillCategories
  - GetSkillCategory
  - ListJobs
  - GetJob
  - SearchJob
  - StandardizeJobs
generated: '2026-08-02'
method: generated
source: openapi/visier-skills-intelligence-engine-openapi.yaml
---

# Extract and match skills with the Visier Skills Intelligence Engine

The Skills Intelligence Engine is a taxonomy plus three inference operations. It authenticates with
an API key header (`x-api-key` — see `authentication/visier-authentication.yml`), independently of
the tenant-scoped platform APIs.

## The taxonomy

Three levels, browsable and searchable:

- `ListSkillCategories` / `GetSkillCategory` (`/v1/skill-categories`) — broadest grouping.
- `ListSkillGroups` / `GetSkillGroup` (`/v1/skill-groups`) — mid-level grouping.
- `ListSkills` / `GetSkill` / `SearchSkill` (`/v1/skills`, `/v1/skills/search`) — the skills.

Jobs have their own library: `ListJobs` / `GetJob` / `SearchJob` (`/v1/jobs`, `/v1/jobs/search`).

Resolve to taxonomy ids before doing anything analytical. Free-text skill strings are not comparable
across sources; taxonomy ids are.

## The three inference operations

### Standardize job titles — `StandardizeJobs` (`POST /v1/jobs/standardize`)

Map messy internal titles ("Sr. Eng II, Platform") onto library jobs. Run this first when working
from an HRIS export, so everything downstream shares one vocabulary.

### Extract skills from text — `ExtractSkills` (`POST /v1/skills/extract`)

Pull taxonomy skills out of free text — a job description, a requisition, a profile. Use it to build
a skills inventory from documents you already have rather than asking people to self-report.

### Match skills to jobs — `MatchSkills` (`POST /v1/skills/match`)

Score how a set of skills fits a job. This is what powers gap analysis, internal mobility
suggestions, and reskilling plans.

## A typical flow

1. `StandardizeJobs` on the job architecture.
2. `ExtractSkills` on each job description.
3. `MatchSkills` between a person's skills and target jobs.
4. Resolve results to `GetSkill` / `GetJob` for names and grouping before reporting.

## Rules

- These are **inferences, not facts**. Extraction and matching produce candidates with confidence.
  Present them as suggestions; keep a human in the loop before anything touches hiring, promotion,
  pay, or termination.
- Extracted skills attach to identifiable people. Handle them as employee data — minimize, do not log
  raw text, and do not forward beyond the requesting system.
- Batch. `ExtractSkills` and `MatchSkills` are POSTs against a 100-call/minute limit; chunk a large
  corpus and pace it from `X-RateLimit-Remaining-Minute`.
- Do not invent skill or job ids. If a search returns nothing, the honest answer is "no taxonomy match".
- This API has no idempotency key; these operations are inferences and safe to retry, but track what
  you have already submitted so you do not re-bill and re-process a corpus.

See `data-model/visier-data-model.yml` and `rate-limits/visier-rate-limits.yml`.
