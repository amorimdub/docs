# mcp.md

**Last verified:** 2026-08-20

This file tells an AI Client or a human how to register an MCP Connection with CompanyOS. Follow it top to bottom. Click-by-click client menus live in [How to connect Claude](/how-to-connect-claude) and [How to connect ChatGPT or Codex](/how-to-connect-chatgpt-codex).

Hosts used below:

- Resource: `https://app.companyos.cc`
- Connection path: `/api/mcp`
- Full connection link: `https://app.companyos.cc/api/mcp`

Preview uses the same path on `https://preview.companyos.cc`.

## How it works

One MCP Connection binds one AI Client to one Member and one Workspace. The client can search and read Company Files and that Member's Personal Files. It cannot see another Member's Personal Files. Connected Integrations add only the curated tools CompanyOS ships for that provider. Writes and sends need Owner approval unless an Owner turns approval off for that connection.

The connection link is not an API key. Sign-in happens in CompanyOS.

## 1. Discover

In CompanyOS, open **AI connections** and copy the connection link. It is always:

```text
https://app.companyos.cc/api/mcp
```

An agent that already has a Workspace session can treat that URL as the remote MCP server. There is no separate client id or client secret.

## 2. Sign in

Paste the connection link where the AI Client asks for a custom connector / remote MCP server URL. Complete CompanyOS sign-in and select the Workspace.

```http
GET /api/mcp HTTP/1.1
Host: app.companyos.cc
```

OAuth binds the caller to the signed-in Member and the Workspace they pick. If no Workspace appears, the account is not a Member of any Workspace, or they signed in with a different email.

## 3. Use

After connect, the AI Client discovers prompts, resources, and tools from CompanyOS. Availability changes with role and which Integrations are connected.

Ask only for knowledge that exists in the Workspace. Do not claim a write or send unless CompanyOS returned a successful result for that operation.

## 4. Verify

In a new conversation, ask something only the Workspace files can answer:

```text
What are the most important things I should know from this workspace? Cite the files you used.
```

A grounded answer names or cites Company Files or the Member's own Personal Files. CompanyOS marks the Workspace grounded-answer check from that observed read, not from a checkbox.

## Errors

If the connector is listed but the client never reads files, enable the connector for that conversation and confirm the Workspace has readable files.

If sign-in succeeds and no Workspace is listed, fix membership before retrying.

Operation errors returned by CompanyOS are in the [AI-Actionable Error catalog](/build-with-companyos/error-catalog).

## Related

- [AI Clients](/ai-clients)
- [How to connect Claude](/how-to-connect-claude)
- [How to connect ChatGPT or Codex](/how-to-connect-chatgpt-codex)
- [Essentials](/essentials)
