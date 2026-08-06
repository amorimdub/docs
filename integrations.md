# Integrations

An Integration is a CompanyOS-brokered connection to an external provider that exposes provider data to AI Clients through curated CompanyOS operations and scoped text.

## Connection Scope

Integrations are either Workspace-Scoped or Member-Scoped:

- **Workspace-Scoped Integrations** are connected once by an Owner and become available to every entitled Member. Examples include shared search APIs, CRMs, or shared file stores.
- **Member-Scoped Integrations** are connected by each Member for their own account. CompanyOS holds the credential and brokers access for that Member across their AI Clients.

## Managed Integrations

For Owner enablement, reconnect lifecycle, curated operations, and ordinary HTTP examples, see [Managed Integrations](/managed-integrations).

## AI Client Connectors

Some providers can also be connected inside the AI Client itself. CompanyOS never holds those credentials and never proxies their data. A Procedure can reference them only through an Input Source Hint.

## How data is exposed

Integration data is exposed as scoped text or through curated Action Platform operations. CompanyOS never embeds raw provider files in MCP resources and never exposes a managed vendor's raw action catalog to AI Clients.
