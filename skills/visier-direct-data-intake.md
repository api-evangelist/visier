---
name: Load data into Visier with Direct Data Intake
description: Run a transactional Direct Data Intake load — inspect the draft config and object schema, start a transaction, load data, then commit or roll back.
api: openapi/visier-data-in-apis-openapi.yaml
operations:
  - DirectDataIntake_GetConfig
  - DirectDataIntake_PutConfig
  - DirectDataIntake_ObjectSchema
  - DirectDataIntake_StartTransaction
  - DirectDataIntake_LoadSampleData
  - DirectDataIntake_JobStatus
  - DirectDataIntake_CommitTransaction
  - DirectDataIntake_RollbackTransaction
  - DirectDataIntake_ListTransactions
generated: '2026-08-02'
method: generated
source: openapi/visier-data-in-apis-openapi.yaml + https://docs.visier.com/developer/apis/data-in/direct-data-intake/direct-data-intake-api.htm
---

# Load data into Visier with Direct Data Intake

Direct Data Intake (DDI) is the one genuinely transactional surface in the Visier API: you start a
transaction, load into it, and then either commit it or roll it back. Nothing lands until commit.
Everything is scoped to a `{draftId}`.

## 1. Authenticate and scope

Follow `visier-authenticate.md`; you need `write` scope. Send `TargetTenantID` when the credential
spans multiple tenants. Get the `{draftId}` from the Visier project you are loading into — do not
guess it.

## 2. Understand what you are loading into

- `DirectDataIntake_GetConfig` (`GET /v1/data/directloads/{draftId}/configs`) — the current load
  configuration.
- `DirectDataIntake_ObjectSchema` (`GET /v1/data/directloads/{draftId}/schemas/{objectName}`) — the
  target object's schema. **Read this before building the payload.** Column names and types come from
  here, not from assumption.
- `DirectDataIntake_PutConfig` (`PUT /v1/data/directloads/{draftId}/configs`) — only when the
  configuration genuinely needs to change; this is a destructive replace.

## 3. Run the transaction

1. `DirectDataIntake_StartTransaction` (`POST /v1/data/directloads/{draftId}/transactions`) — keep
   the returned `transactionId`. Everything below depends on it.
2. Load the data for each object in the transaction. `DirectDataIntake_LoadSampleData`
   (`POST /v1/data/directloads/{draftId}/transactions/{transactionId}/{objectName}/sample-data`)
   is the path for sample/small payloads.
3. `DirectDataIntake_JobStatus`
   (`GET /v1/data/directloads/{draftId}/transactions/{transactionId}`) — poll until the load work is
   finished. Do not commit while it is still running.
4. Finish, always:
   - `DirectDataIntake_CommitTransaction`
     (`POST /v1/data/directloads/{draftId}/transactions/{transactionId}`) on success, or
   - `DirectDataIntake_RollbackTransaction`
     (`DELETE /v1/data/directloads/{draftId}/transactions/{transactionId}`) on any failure.

`DirectDataIntake_ListTransactions` (`GET /v1/data/directloads/{draftId}/transactions`) shows what is
open — use it to find and clean up an abandoned transaction before starting a new one.

## 4. Know when the data is queryable

Committing a transaction does not make data queryable. Visier must process and publish a **data
version**. Watch for it with the `dvPublish` webhook event, or poll
`DataAndJobHandling_LatestEnabledDV` (`GET /v1/op/data-versions`). See
`visier-subscribe-to-platform-events.md`.

## Rules

- **There is no idempotency key on this API.** A retried start-transaction creates a *second*
  transaction. Track the `transactionId` you already have and reuse it; never blind-retry a POST.
- Never leave a transaction open. If any step fails and you cannot recover, roll back.
- "Request Data is Malformed" (400) means format or size limits were exceeded — check the object
  schema and the documented data size limits rather than retrying the same payload.
- "Expected Data Version is Not Available" means the tenant needs a new data version generated and
  published.
- Report the `rci` from any error response; that is what Visier support traces.
- This API moves real HR data. Do not log payload rows.

See `conventions/visier-conventions.yml` and `errors/visier-problem-types.yml`.
