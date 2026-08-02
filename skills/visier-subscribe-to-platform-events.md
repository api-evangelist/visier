---
name: Subscribe to Visier platform events with webhooks
description: Register an HTTPS endpoint with Visier, subscribe to the right event types, test delivery, and monitor webhook health — instead of polling job status.
api: openapi/visier-webhooks-openapi.yaml
operations:
  - Webhooks_GetAllWebhooks
  - Webhooks_CreateWebhook
  - Webhooks_GetWebhook
  - Webhooks_UpdateWebhook
  - Webhooks_DeleteWebhook
  - Webhooks_UpdateWebhookCredentials
  - Webhooks_DeleteWebhookCredentials
  - Webhooks_SendTestEvent
  - Webhooks_GetWebhooksStatus
generated: '2026-08-02'
method: generated
source: openapi/visier-webhooks-openapi.yaml + https://docs.visier.com/developer/apis/webhooks/webhooks-api.htm
---

# Subscribe to Visier platform events with webhooks

The Webhooks API (Beta) lets Visier push to you instead of you polling. This is the correct way to
learn that a load finished or a data version published.

## 1. Authenticate

Follow `visier-authenticate.md`; you need `write` scope and administrative capability. Send
`TargetTenantID` when the credential spans multiple tenants.

## 2. Pick the event types

| Event | Fires when |
|---|---|
| `jobResultSuccess` | A job completed successfully |
| `jobResultFailure` | A job failed to complete |
| `jobReschedule` | A job was rescheduled |
| `dvPublish` | A data version published to production |
| `alertNotification` | A personalized alert notification was triggered |
| `smartCompNotification` | A Smart Compensation event fired (Embedded Partners) |
| `dataUploadNotification` | A data file was uploaded |
| `systemAlertNotification` | A system event alert fired |
| `planRowPromotionNotification` | A row in a plan was promoted |
| `auditEvent` | An audit event was triggered |

Subscribe to what you will act on. `jobResultSuccess` + `jobResultFailure` replace polling
`DataAndJobHandling_JobStatus`; `dvPublish` is the signal that newly loaded data is queryable.

## 3. Register and verify

1. `Webhooks_GetAllWebhooks` (`GET /v1/op/webhooks`) — check whether one already exists before
   creating a duplicate.
2. `Webhooks_CreateWebhook` (`POST /v1/op/webhooks`) — supply your HTTPS URL, active flag, and event
   types. Credentials (basic auth) are stored separately and referenced by `credentialReference`.
3. `Webhooks_SendTestEvent` (`POST /v1/op/webhooks/{webhookId}/testEvent`) — **always do this.** Do
   not declare the integration done until a test event has been received at your endpoint.
4. `Webhooks_GetWebhook` (`GET /v1/op/webhooks/{webhookId}`) — confirm the stored definition.

## 4. Operate it

- `Webhooks_GetWebhooksStatus` (`GET /v1/op/webhooks-status`) — delivery health. Poll this on a
  schedule; a silently failing webhook looks identical to "nothing happened".
- `Webhooks_UpdateWebhook` (`PUT /v1/op/webhooks/{webhookId}`) to change URL or event list.
- `Webhooks_UpdateWebhookCredentials` (`PUT /v1/op/webhooks/{webhookId}/credentials`) to rotate the
  basic-auth credential. Rotate on a schedule; delete with
  `Webhooks_DeleteWebhookCredentials` when decommissioning.
- `Webhooks_DeleteWebhook` (`DELETE /v1/op/webhooks/{webhookId}`) when retiring the integration.

## Rules

- Your endpoint must be HTTPS and must authenticate the caller with the credentials you registered —
  an unauthenticated receiver will accept forged events.
- Visier does not publish event payload schemas in the OpenAPI (only the subscription shapes). Treat
  the payload defensively: validate before use, and use the event as a *trigger* to call the API for
  authoritative state rather than trusting the payload as the record.
- Respond fast and process asynchronously; do work after acknowledging.
- Handle redelivery — assume at-least-once, and make your handler safe to run twice, because there is
  no idempotency key anywhere in this API.
- The API is **Beta**. Pin to it deliberately and watch the release notes.

See `asyncapi/visier-webhooks.yml` and `lifecycle/visier-lifecycle.yml`.
