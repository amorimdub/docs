# How to set up CompanyOS

**Last verified:** 2026-08-20

Give this page to anyone connecting Claude, ChatGPT, or Codex to a CompanyOS Workspace. Grok is not a supported client.

## What to copy

Connection link (this is the MCP server URL):

```text
https://app.companyos.cc/api/mcp
```

Test question:

```text
What are the most important things I should know from this workspace? Cite the files you used.
```

There is no client id or client secret. Sign-in happens in CompanyOS after you paste the link.

If a client asks for a context or token allowance, set it to **50,000**.

## How it works

One connection binds one AI client to one Member and one Workspace. The client can search and read Company Files and that Member's Personal Files. It cannot see another Member's Personal Files. Writes and sends need Owner approval unless an Owner turns approval off for that connection.

The connection link is not an API key.

## Claude

1. Copy `https://app.companyos.cc/api/mcp`.
2. In Claude, open **Customize → Connectors → Add → Add custom connector**.
3. Name it `CompanyOS`. Paste the connection link as the remote MCP server URL. Leave Advanced settings empty.
4. Click **Add**, sign in to CompanyOS, and select the Workspace.
5. Enable the connector for the chat. Ask the test question above.

Click-by-click screenshots: [How to connect Claude](/how-to-connect-claude).

## ChatGPT

1. Copy `https://app.companyos.cc/api/mcp`.
2. Turn on **Developer mode** (Settings → Security, or Settings → Plugins).
3. Add a custom connector / plugin and paste the connection link.
4. Sign in to CompanyOS and select the Workspace.
5. If ChatGPT asks for a context or token allowance, enter **50000**.
6. Ask the test question above.

Developer mode is ChatGPT's setting, not CompanyOS. If you do not want it on, use Claude instead. Details: [How to connect ChatGPT or Codex](/how-to-connect-chatgpt-codex).

## Codex (CLI, desktop, IDE)

Add a Streamable HTTP server named `companyos` with the connection link, then authenticate.

```toml
[mcp_servers.companyos]
url = "https://app.companyos.cc/api/mcp"
startup_timeout_sec = 20
tool_timeout_sec = 120
```

```bash
codex mcp login companyos
```

Or in the ChatGPT desktop app / IDE: Settings → MCP servers → Add server → Streamable HTTP → paste `https://app.companyos.cc/api/mcp` → Authenticate.

Type `/mcp` in Codex to confirm `companyos` is connected.

## Codex Cloud

Codex Cloud runs in a hosted environment. The same URL applies.

1. Open [Codex Cloud environments](https://chatgpt.com/codex/settings/environments).
2. Enable **agent internet access** so the environment can reach `app.companyos.cc`.
3. Add the CompanyOS MCP server:
   - Name: `companyos`
   - Type: Streamable HTTP
   - URL: `https://app.companyos.cc/api/mcp`
4. If the environment asks for a context or token allowance, set **50000**.
5. Complete CompanyOS sign-in and select the Workspace.
6. Start a cloud chat and ask the test question.

Without internet access, Codex Cloud cannot reach CompanyOS.

## Verify

A listed connector is not enough. Ask the test question. A grounded answer cites your Company Files or your own Personal Files. CompanyOS marks the Workspace check from that read.

## Errors

- **No Workspace after sign-in.** The account is not a Member, or you signed in with a different email.
- **Connector listed but no files.** Enable the connector for this conversation and confirm the Workspace has readable files.
- **Codex Cloud cannot connect.** Turn on agent internet access, then retry.

More: [AI-Actionable Error catalog](/build-with-companyos/error-catalog).
