---
name: Authenticate against the Visier API
description: Obtain a Visier API credential — either a secure token via basic authentication or an OAuth 2.0 JWT — and attach it correctly to every subsequent call.
api: openapi/visier-authentication-apis-openapi.yaml
operations:
  - BasicAuthentication_ASIDTokenAuthentication
  - OAuth2_OAuth2Authorize
  - OAuth2_OAuth2Token
  - OAuth2_UserInfo
  - BasicAuthentication_GenerateImpersonationToken
generated: '2026-08-02'
method: generated
source: openapi/visier-authentication-apis-openapi.yaml + https://docs.visier.com/developer/apis/headers.htm
---

# Authenticate against the Visier API

Every Visier API call needs **two** things: an API key, and a token. The API key alone is never
enough, and the token alone is never enough.

## 0. Resolve the host

Visier has no shared API host. The base URL is `https://{vanity_name}.api.visier.io`, where
`{vanity_name}` is the tenant's vanity name. Find it in Visier under **Settings → Single Sign-On**:
a service provider endpoint of `https://jupiter.visier.com/VServer/auth` means the vanity name is
`jupiter`. If you do not have the vanity name, stop and ask for it — do not guess.

## 1. Always send the API key

    apikey: {api_key}

This header is required on **all** API calls, including the token requests below.

## 2. Pick a token method

### Basic authentication (secure token)

Call `BasicAuthentication_ASIDTokenAuthentication` (`POST /v1/admin/visierSecureToken`) with the
username and password. The response is a Visier secure token. Send it as a cookie on every call:

    apikey: {api_key}
    Cookie: VisierASIDToken={security_token}

Use this for service accounts and simple scripts.

### OAuth 2.0 (recommended for applications)

Register a client application in Visier first, to get a client ID, client secret and redirect URI.

- **Authorization code grant** (a user is present): send the user to `OAuth2_OAuth2Authorize`
  (`GET /v1/auth/oauth2/authorize`), then exchange the code at `OAuth2_OAuth2Token`
  (`POST /v1/auth/oauth2/token`).
- **Password grant** (service account, no user): call `OAuth2_OAuth2Token` directly with the
  username and password plus client credentials.

Scopes are `read` and `write` — request the narrower one when you only query.

Attach the resulting JWT:

    apikey: {api_key}
    Authorization: Bearer {jwt}

Call `OAuth2_UserInfo` (`GET /v1/auth/oauth2/userinfo`) to confirm which user the token represents.

### Impersonation

`BasicAuthentication_GenerateImpersonationToken` (`POST /v1/admin/visierImpersonationToken`) issues a
token that lets an authorized caller act as another user. Send it as
`Cookie: VisierImpersonationToken={token}`. Only use this when the integration is explicitly designed
for it — it inherits the impersonated user's data access.

## 3. Target the right tenant and project

If the credential can see more than one tenant, name the tenant explicitly:

    TargetTenantID: {tenant_id}

If the call changes the analytic model or administration objects, it runs inside a project:

    ProjectID: {project_uuid}

## Rules

- A 401 means the credentials **expired**, not that they were wrong. Re-authenticate and retry once;
  do not loop.
- A 403 means the caller is authenticated but lacks a capability, analytic permission, data access
  set, or tenant access. That is a Visier administrator's job to grant — retrying will not fix it.
- OAuth access tokens issued for the Visier Query MCP server live 60 minutes; refresh rather than
  re-running the full authorization flow.
- Never log the API key, the secure token, or the JWT.

See `authentication/visier-authentication.yml` and `scopes/visier-scopes.yml`.
