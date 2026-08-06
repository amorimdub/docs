# Managed Integrations

**Last verified:** 2026-07-17

A Managed Integration is a CompanyOS-brokered connection to an external provider. CompanyOS holds the connection through its managed Auth + Proxy plane, then exposes only curated, CompanyOS-shipped operations to Members and AI Clients.

CompanyOS uses Nango as its managed Auth + Proxy plane. A CompanyOS provider manifest decides each provider's Connection Scope, approved connection flow, and curated operations before it appears in your Workspace. CompanyOS never exposes Nango's raw action catalog, write toolbox, or uncurated proxy surface to AI Clients. Connecting a provider stores the connection; AI Clients only see the semantic operations CompanyOS has approved for that provider.

## Connection Scope

Every Integration has a **Connection Scope**:

| Scope | Who connects | Who can use curated operations | Who disconnects |
| --- | --- | --- | --- |
| **Workspace-Scoped** | Owner, once for the Workspace | Entitled Members through CompanyOS | Owner |
| **Member-Scoped** | Each Member for their own account | That Member across their AI Clients | That Member |

Examples of scope choices:

- Shared search APIs and shared CRMs are typically **Workspace-Scoped**.
- A personal mailbox is **Member-Scoped** so credentials and mail stay with the connecting Member.

Scope is decided per provider by CompanyOS. Members cannot re-scope a Workspace connection, and Owners cannot attach another Member's personal connection as Workspace-wide.

## Owner enablement

1. Open the Workspace **Integrations** area.
2. Choose a provider that CompanyOS lists as available for your Workspace.
3. Start connect. Complete the provider sign-in or API-key flow CompanyOS starts.
4. Confirm status shows **connected** for the correct scope.
5. Verify an AI Client can call only the curated operations for that provider.

Workspace-Scoped connections require an Owner. Member-Scoped connections are started by the Member who owns the credential. Owners enable Workspace-level Integrations; they do not need to re-connect a Member-Scoped mailbox on behalf of every Member.

## Reconnect lifecycle

Connections can enter a **needs reconnect** state when the provider revokes access, a refresh fails, or the managed plane reports a lifecycle event.

When a connection needs reconnect:

1. Curated operations for that connection stop advertising or fail with AI-Actionable Errors that point at reconnect.
2. The owning Owner (Workspace-Scoped) or Member (Member-Scoped) restarts connect from CompanyOS.
3. After a successful reconnect, curated operations return for that scope only. Other Workspaces are unaffected; for a Member-Scoped connection, other Members are unaffected. A Workspace-Scoped connection affects every entitled Member in its Workspace.

CompanyOS does not promise seamless credential migration between managed hosting modes. If operators move the Auth + Proxy plane (for example Cloud trial to self-host), design partners reconnect through CompanyOS rather than expecting silent token transfer.

## Curated operations only

After connect:

- AI Clients discover tools through MCP or capability discovery (`GET /api/v1/operations`).
- Only CompanyOS-curated operation IDs appear (for example Microsoft 365 read and send operations that CompanyOS ships).
- Raw vendor proxy endpoints, uncurated catalogs, and arbitrary write actions from the managed plane are not product surface.

Treat capability discovery as the source of truth for what is available in a given Workspace and role.

## Ordinary HTTP examples

Managed Integration **connection** happens in the CompanyOS web app (or the Workspace Integrations APIs that start connect sessions). Automations that **use** a connected provider still call ordinary Action Platform HTTP with no CompanyOS SDK.

Authenticate with a Member session token or Automation Grant secret as `Authorization: Bearer …`.

### Discover available operations

#### curl

```bash
curl -sS "https://app.companyos.cc/api/v1/operations" \
  -H "Authorization: Bearer $COMPANYOS_TOKEN"
```

#### TypeScript (fetch)

```ts
const response = await fetch("https://app.companyos.cc/api/v1/operations", {
  headers: { Authorization: `Bearer ${process.env.COMPANYOS_TOKEN}` },
});
const body = await response.json();
// body.operations → [{ id, title, availability, … }, …]
```

#### Python (urllib)

```python
import json
import os
import urllib.request

req = urllib.request.Request(
    "https://app.companyos.cc/api/v1/operations",
    headers={"Authorization": f"Bearer {os.environ['COMPANYOS_TOKEN']}"},
    method="GET",
)
with urllib.request.urlopen(req) as res:
    body = json.load(res)
# body["operations"]
```

### Call a curated Integration operation

Use the operation ID returned by discovery. Microsoft 365 list-send-history is one curated example:

Operation ID: `m365.list_send_history`

#### curl

```bash
curl -sS -X POST "https://app.companyos.cc/api/v1/operations/m365.list_send_history" \
  -H "Authorization: Bearer $COMPANYOS_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{}'
```

#### TypeScript (fetch)

```ts
const response = await fetch(
  "https://app.companyos.cc/api/v1/operations/m365.list_send_history",
  {
    method: "POST",
    headers: {
      Authorization: `Bearer ${process.env.COMPANYOS_TOKEN}`,
      "Content-Type": "application/json",
    },
    body: JSON.stringify({}),
  },
);
const body = await response.json();
```

#### Python (urllib)

```python
import json
import os
import urllib.request

req = urllib.request.Request(
    "https://app.companyos.cc/api/v1/operations/m365.list_send_history",
    data=json.dumps({}).encode(),
    headers={
        "Authorization": f"Bearer {os.environ['COMPANYOS_TOKEN']}",
        "Content-Type": "application/json",
    },
    method="POST",
)
with urllib.request.urlopen(req) as res:
    body = json.load(res)
```

If the Member-Scoped mailbox needs reconnect, the response is an AI-Actionable Error that tells the Member to reconnect Microsoft 365 in CompanyOS—not to paste tokens into the AI Client.

## Related

- [Integrations](/integrations) — product overview of Integration data exposure
- [Email](/email) — lifecycle mail and Approval Links
- [Automation](/automation) — Automation Grants for unattended callers
- [OpenAPI reference](/build-with-companyos/openapi)
