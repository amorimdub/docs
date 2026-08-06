# How to connect Claude

**Last verified:** 2026-08-06

Claude is the recommended AI Client for CompanyOS. This page is the click-by-click path. For what an AI Client is and what it can see, read [AI Clients](/ai-clients).

Setup takes about five minutes and happens mostly inside Claude's own settings.

## Before you start

- You are signed in to CompanyOS as a Member or Owner of the Workspace you want to connect.
- The Workspace already has at least one readable Company File. Connecting an empty Workspace works, but the grounded-answer check at the end will return nothing useful.
- Claude currently permits one custom connector on the Free plan. Paid plans permit more.

## Steps

1. In CompanyOS, open **AI Clients** and copy the connection link for your Workspace. It is `https://app.companyos.cc/api/mcp`.
2. In Claude, open **Customize → Connectors**.

   Connectors moved out of Settings. If you open **Settings → Connectors** you will see only the message "Connectors have moved to Customize" with a link across — follow it.
3. Click **Add** in the top right of the Connectors panel, then choose **Add custom connector** from the dropdown.
4. In the **Add custom connector** dialog, fill in two fields:

   - **Name** — anything you will recognise later, for example `CompanyOS`.
   - **Remote MCP server URL** — paste the connection link from step 1.

   Leave **Advanced settings** alone. The **OAuth Client ID** and **OAuth Client Secret** fields are optional and CompanyOS does not require them.
5. Click **Add**.
6. Complete the sign-in flow when Claude opens it, and select the correct Workspace if you belong to more than one.
7. Back in **Customize → Connectors**, confirm your connector is listed with type **Web**, a **Custom** tag, and a checkmark in the Status column.

## Verify the connection

A connector that appears in the list is configured, not proven. Activation completes only when CompanyOS observes a real knowledge read.

In a new Claude chat, ask something only your Workspace files can answer:

```
Summarize the launch plan and cite the files you used.
```

A grounded answer names or cites your Company Files or your own Personal Files. A generic answer means Claude did not read from CompanyOS — check that the connector is enabled for the conversation and that the Workspace has relevant files.

Return to Workspace Home. CompanyOS marks **Verify a grounded answer** complete from the observed read, not from a checkbox.

## If the screen does not match

Claude's connector menus and labels change without notice, and this page carries the date it was last checked. If a label above no longer exists, look for the current "custom connector" or "MCP" flow anywhere in Claude's settings and use the same connection link — the endpoint is what matters, not the route to the form.

## Troubleshooting

**The connector is listed but Claude never uses it.** Check that the connector is enabled for the conversation. Some Claude surfaces require selecting the connector explicitly before it is available to a chat.

**Sign-in succeeds but no Workspace appears.** Your account may not be a Member of any Workspace yet, or you signed in with a different email than your membership. Memberships are per-Workspace and per-email.

**Claude sees no files.** Confirm the files are Company Files, or Personal Files you added yourself. Claude cannot see another Member's Personal Files.

For error identifiers returned by CompanyOS operations, see the [AI-Actionable Error catalog](/build-with-companyos/error-catalog).

## Related pages

- [AI Clients](/ai-clients)
- [Essentials](/essentials)
- [How to connect ChatGPT or Codex](/how-to-connect-chatgpt-codex)
- [How to schedule a Claude Cowork routine](/how-to-schedule-a-claude-cowork-routine)
