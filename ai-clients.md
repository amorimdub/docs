# AI Clients

An AI Client is an external assistant or agent application that connects to CompanyOS to work with the Workspace knowledge visible to you.

## Connect one

- [How to connect Claude](/how-to-connect-claude) — recommended primary path.
- [How to connect ChatGPT or Codex](/how-to-connect-chatgpt-codex) — supported alternative.

Connecting **one** supported client is enough to activate a Workspace. See [Essentials](/essentials) for where connection sits in the activation sequence.

## Supported AI Clients

CompanyOS is Claude-first and supports compatible AI Clients that use MCP Connections:

- Claude (recommended primary path)
- ChatGPT (supported alternative)
- Codex and other compatible clients (supported alternative)

**Last verified:** 2026-08-06 — Claude currently permits one custom connector on Free. ChatGPT reaches custom MCP connectors through Developer mode; availability differs by plan, so check your own account. Codex availability can differ again; check its current connector requirements before setup.

## MCP Connection

An MCP Connection links an AI Client to a selected Workspace.

The connection is a **scoped action surface**, not a uniformly read-only one. What an AI Client may do depends on the Member's role, the operations CompanyOS has curated, and the consent or grant backing each call:

- **Source files and provider content are read-only.** An AI Client can search and read what is visible to you. It cannot rewrite your uploaded files, and it never sees a raw provider catalog — only CompanyOS-curated operations.
- **Some operations write or send.** Owners can author Procedure Content. Authorized Members can send Microsoft 365 mail and push Workspace Records. Each such operation is separately authorized.
- **External and destructive effects need explicit authorization.** An interactive call uses a one-time approval bound to the exact payload; an unattended call uses a revocable Automation Grant. Neither can stand in for the other, and authority is rechecked on every invocation.
- **Every write is recorded.** Writes enter a privacy-preserving Action Log.

Treat capability discovery as the source of truth for what is actually available in a given Workspace and role. An AI Client should never claim a side effect it did not receive a successful result for.

## What AI Clients can see

AI Clients receive only the knowledge visible to the Member who set up the connection:

- All Company Files in the Workspace.
- The Member's own Personal Files.
- Read-only provider content from Workspace-Scoped Integrations.
- Member-Scoped Integrations connected by that Member.

AI Clients cannot see another Member's Personal Files.

## Procedure Authoring Tools

Owners can use MCP tools that create draft Procedure Content and edit published content. The first publish must be reviewed in the web UI; later Owner edits publish directly.

## Related pages

- [Essentials](/essentials)
- [Knowledge](/knowledge)
- [How search works](/how-search-works)
- [Permissions](/permissions)
- [Permissions](/permissions)
- [Routines](/routines)
