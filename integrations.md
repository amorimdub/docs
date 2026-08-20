# Integrations

An Integration is a CompanyOS-brokered connection to an external provider that exposes provider data to AI Clients through curated CompanyOS operations and scoped text.

## Workspace catalog

Integrations is a fixed Workspace catalog, not a live provider directory. Always-visible rows:

- **SharePoint Online** — an Owner connects with delegated site read, then picks sites.
- **Airtable** — an Owner pastes a Personal Access Token.
- **Exa** — an Owner pastes a read-only API key on the Exa sheet.

Personal Microsoft 365 mail lives on **Mailbox**, not in this catalog. There is no Directory tab, no Add picker, and no Bring-your-own create.

## Connection Scope

- **Workspace Connection** — an Owner connects once for the Workspace. Entitled Members can use the curated operations.
- **Personal Connection** — a Member connects their own account. Credentials stay with that Member. Mailbox Microsoft 365 is this kind of connection.

## Managed Integrations

For Owner enablement, reconnect lifecycle, and ordinary HTTP examples, see [Managed Integrations](/managed-integrations).

## How data is exposed

Integration data is exposed as scoped text or through curated Action Platform operations. CompanyOS never embeds raw provider files in MCP resources and never exposes a managed vendor's raw action catalog to AI Clients.
