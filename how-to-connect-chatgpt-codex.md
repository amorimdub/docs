# How to connect ChatGPT or Codex

**Last verified:** 2026-08-06

ChatGPT and Codex are supported alternatives to Claude. Connecting one supported AI Client is enough to activate a Workspace — you do not need both. For the recommended path, see [How to connect Claude](/how-to-connect-claude).

## Before you start

- You are signed in to CompanyOS as a Member or Owner of the Workspace you want to connect.
- Custom MCP connectors in ChatGPT are added through **Developer mode**, which ChatGPT labels **ELEVATED RISK**. ChatGPT's own warning is that it "allows you to add unverified connectors that could modify or erase data permanently." That warning is about the general capability, not about CompanyOS specifically — but read the next section before enabling it.

## What Developer mode means for your data

Turning on Developer mode changes what *any* connector you add can do, not just this one. CompanyOS knowledge access is read-only for source files and provider content: an AI Client can search and read what is visible to you, and cannot rewrite your uploaded files. Operations that write or send exist, but each one is separately authorized and, where it has an external effect, requires an explicit approval you grant at the time.

If you are not comfortable enabling Developer mode on your account, use [Claude](/how-to-connect-claude) instead — it reaches the same CompanyOS knowledge without this setting.

## Steps

1. In CompanyOS, open **AI Clients** and copy the connection link for your Workspace. It is `https://app.companyos.cc/api/mcp`.
2. In ChatGPT, open **Settings → Security and login** and scroll to the **Developer mode** section.

   ChatGPT renamed Connectors to **Plugins**. You can also reach this from **Settings → Plugins**, scrolling to the bottom of the plugin list, and choosing **Developer mode**.
3. Turn on the **Developer mode** toggle.
4. Go to **Settings → Plugins** and add a custom connector using the connection link from step 1.
5. Complete the OAuth sign-in flow and select the correct Workspace if you belong to more than one.
6. Confirm the connector appears in the plugin list as connected.

## Verify the connection

In a new ChatGPT conversation, ask something only your Workspace files can answer:

```
What do you know about this Workspace? Cite sources.
```

A grounded answer names or cites your Company Files or your own Personal Files. Return to Workspace Home — CompanyOS marks **Verify a grounded answer** complete from the observed read, not from a checkbox.

## Codex

Codex uses the same connection link and the same OAuth flow. Its connector settings differ from the ChatGPT web app and change more often than either Claude's or ChatGPT's, so check Codex's current connector requirements before setup rather than assuming the steps above transfer.

Codex is not a hosted scheduling path. See [Routines](/routines) for what runs without your computer.

## Plan availability

Custom MCP connectors were reachable on a ChatGPT Pro account on the date at the top of this page. Availability differs across Free, Plus, Pro, Business, Enterprise, and Edu, and OpenAI changes it — check your own account rather than relying on this line. CompanyOS does not promise universal plan support.

## If the screen does not match

ChatGPT's settings have been reorganised more than once, including the Connectors-to-Plugins rename above. If a label here no longer exists, look for the current custom-MCP or developer-connector flow anywhere in ChatGPT's settings and use the same connection link.

## Related pages

- [AI Clients](/ai-clients)
- [Essentials](/essentials)
- [How to connect Claude](/how-to-connect-claude)
- [AI-Actionable Error catalog](/build-with-companyos/error-catalog)
