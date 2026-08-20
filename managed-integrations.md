# Managed Integrations

**Last verified:** 2026-08-20

A Managed Integration is a CompanyOS-brokered connection to an external provider. CompanyOS holds the connection through its managed Auth + Proxy plane, then exposes only curated, CompanyOS-shipped operations to Members and AI Clients.

CompanyOS uses Nango as its managed Auth + Proxy plane. A CompanyOS provider manifest decides each provider's Connection Scope, approved connection flow, and curated operations before it appears in your Workspace. CompanyOS never exposes Nango's raw action catalog to AI Clients.

## Workspace catalog

The Integrations page lists CompanyOS-owned providers plus Exa. Owners open a row and connect from the side sheet.

| Row | How you connect |
| --- | --- |
| SharePoint Online | Owner signs in. CompanyOS requests delegated `Sites.Read.All`. Then pick which sites to ingest. |
| Airtable | Owner pastes a Personal Access Token. |
| Exa | Owner pastes a read-only API key. |

Personal Microsoft 365 is not a catalog row. Connect it from **Mailbox**.

There is no live scrape of Nango's provider directory, no Bring-your-own create, and no Advanced Setup section.

## Connection Scope

| Scope | Who connects | Who can use curated operations | Who disconnects |
| --- | --- | --- | --- |
| **Workspace-Scoped** | Owner, once for the Workspace | Entitled Members through CompanyOS | Owner |
| **Member-Scoped** | Each Member for their own account | That Member across their AI Clients | That Member |

Shared search APIs and shared file stores are typically **Workspace-Scoped**. A personal mailbox is **Member-Scoped** so credentials and mail stay with the connecting Member.

A Workspace-Scoped connection affects every entitled Member in its Workspace.

## Owner enablement

1. Open the Workspace **Integrations** area.
2. Open a catalog row.
3. Complete the provider sign-in or paste the API key.
4. Confirm status shows **connected**.
5. For SharePoint, select the sites to ingest.

## Reconnect lifecycle

A connection **needs reconnect** only when the provider connection still exists and the token must be refreshed.

If the provider setup is gone, or the Owner already disconnected, CompanyOS removes the local row. The catalog then shows **Connect**, not Reconnect. Start a new connection.

When a live connection needs reconnect:

1. Curated operations for that connection stop until someone reconnects.
2. The owning Owner (Workspace-Scoped) or Member (Member-Scoped) restarts connect from CompanyOS.
3. After a successful reconnect, curated operations return for that scope only.

## Curated operations only

After connect:

- AI Clients discover tools through MCP or capability discovery (`GET /api/v1/operations`).
- Only CompanyOS-curated operation IDs appear.
- Raw vendor proxy endpoints are not product surface.

## Ordinary HTTP examples

Managed Integration **connection** happens in the CompanyOS web app. Automations that **use** a connected provider still call ordinary Action Platform HTTP with no CompanyOS SDK.

Authenticate with a Member session token or Automation Grant secret as `Authorization: Bearer …`.

### Discover available operations

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
```

### Call a curated Integration operation

Microsoft 365 list-send-history is one curated example. Operation ID: `m365.list_send_history`

```bash
curl -sS -X POST "https://app.companyos.cc/api/v1/operations/m365.list_send_history" \
  -H "Authorization: Bearer $COMPANYOS_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{}'
```

If the Member-Scoped mailbox needs reconnect, the response is an AI-Actionable Error that tells the Member to reconnect Microsoft 365 in CompanyOS—not to paste tokens into the AI Client.

## Related

- [Integrations](/integrations)
- [Email](/email)
- [Automation](/automation)
- [OpenAPI reference](/build-with-companyos/openapi)
