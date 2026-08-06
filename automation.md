# Automation

**Last verified:** 2026-07-17

Automation in CompanyOS lets a Workspace run unattended actions through the Action Platform using tightly scoped credentials. Start with Essentials and Procedures first; treat Automation as an optional third learning level.

## Action Platform

The Action Platform exposes operations that AI Clients, routines, and automations can call. Each operation declares availability, required roles, deprecation metadata, and input/output contracts.

Callers use ordinary HTTP against `/api/v1/operations/{operation_id}`. There is no CompanyOS language SDK—use curl, Python's standard library, or TypeScript `fetch`.

## Capability discovery

Callers can discover available operations through `GET /api/v1/operations` or the MCP `tools/list` endpoint. Discovery respects the caller's role and any granted operation scope. Treat the discovery response as authoritative for capability identifiers.

## Automation Grants

An Automation Grant lets an unattended process authenticate as a Member for a specific allowed operation. Grants expire, can be revoked, and must not be embedded in client-side code or public repositories.

Pass the grant secret as `Authorization: Bearer <secret>` when calling Action Platform HTTP routes.

## Audit

Action Platform writes are recorded for audit. Each execution includes the caller identity, operation, payload summary, and result. Sensitive content such as email bodies is hashed or omitted according to each operation's privacy rules.

## Guides in this area

- [Workspace Record Store](/record-store) — Collection push, get, and history with HTTP examples
- [Managed Integrations](/managed-integrations) — Connection Scope, Owner enablement, reconnect, and curated operations

## Related developer reference

- [Build with CompanyOS](/build-with-companyos/index)
- [OpenAPI reference](/build-with-companyos/openapi)
- [AI-Actionable Error Catalog](/build-with-companyos/error-catalog)
