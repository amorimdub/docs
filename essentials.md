# Essentials

**Last verified:** 2026-07-16

Essentials are the three outcomes that activate a Workspace: put real knowledge in place, connect one AI Client, and verify a grounded answer. Only Essentials count as activation. Repeatable work and automation come after.

The in-app Essentials list is dismissible, but dismissing it does not mark a step complete. CompanyOS records completion from server-observed outcomes only (readable files, a successful MCP Connection, and a real knowledge read).

## What a Workspace is

A **Workspace** is the isolated CompanyOS boundary for your company, department, family, or other group. It has its own Members, Company Files, Personal Files, Integrations, CompanyOS Procedures, and AI Client connections.

- **Owners** manage Workspace-wide files, published CompanyOS Procedures, settings, and Workspace-level Integrations.
- **Members** use the knowledge visible to them and may add Personal Files of their own.

Create one Workspace for the group that should share the same Company Brain. Do not invent a separate product concept for each piece of work—stay inside the Workspace you already created.

## Company Files and Personal Files

| Kind | Who can see it | Typical use |
| --- | --- | --- |
| **Company File** | Every Member of the Workspace, and every AI Client connected for that Member | Handbooks, process docs, shared notes your team already relies on |
| **Personal File** | Only the Member who added it (and that Member's AI Client) | Private notes, drafts, or context that should not be shared |

**Folders** group files for navigation. They are not a separate permission boundary.

### Owner path: add useful company knowledge

1. Open **Company Files** in your Workspace.
2. Upload one real document your team already asks about—not a placeholder.
3. Confirm the file appears as readable. CompanyOS counts this step when at least one file is readable by AI, not when you only open the upload screen.

### Member path: understand what your AI can see

1. Open **Company Files** and note what the Workspace already shares.
2. Optionally add a **Personal File** for context only you should use.
3. Remember: your AI Client can search and read Company Files plus your own Personal Files. It cannot see another Member's Personal Files.

## Connect one AI Client (Claude primary, ChatGPT/Codex alternative)

An **AI Client** is an external assistant that connects to CompanyOS through an **MCP Connection**. CompanyOS is **Claude-first**: Claude is the recommended guided path. **ChatGPT** and **Codex** are supported alternatives. Connecting **one** supported client is enough for Essentials.

**Connection Link:** `https://app.companyos.cc/api/mcp`

Open **AI Clients** in the app and copy the Connection Link shown for your Workspace.

### Step-by-step setup

The click-by-click paths live in their own how-tos, because third-party connector menus change and those pages carry the date they were last checked:

- [How to connect Claude](/how-to-connect-claude) — recommended.
- [How to connect ChatGPT or Codex](/how-to-connect-chatgpt-codex) — alternative.

Setup usually takes 5–10 minutes the first time, mostly inside the AI Client's own UI.

**Claude-ready** means CompanyOS has the Connection Link needed for Claude setup. It does not confirm that setup is complete inside Claude.

Knowledge access over MCP is read-only for source files and provider content. Explicitly authorized operations may write or send — see [AI Clients](/ai-clients) for the full scoped action surface.

## Verify a grounded answer

Activation completes only after your AI Client performs a **real knowledge read** against Workspace files—not after you click a tutorial link.

1. In your connected AI Client, ask something that only your files can answer, for example:

   - `Summarize the launch plan and cite the files you used.`
   - `What do you know about this Workspace? Cite sources.`
2. Confirm the answer is **grounded**: it should draw on your Company Files or Personal Files and cite or name those sources.
3. If the answer is empty or generic, add a more relevant file and try again. An empty read means coverage is thin, not that the product is finished for you.
4. Return to Workspace Home. CompanyOS marks **Verify a grounded answer** complete when the server observes a successful in-scope read (`lastReadByAiClientAt`), not when you mark a checkbox yourself.

## Owner and Member Essentials at a glance

### Owner Essentials

1. **Add useful company knowledge** — upload one real Company File.
2. **Connect one AI client** — Claude recommended; ChatGPT or Codex also work.
3. **Verify a grounded answer** — confirm a source-backed reply from your files.

### Member Essentials

1. **Understand what your AI can see** — Company Files vs Personal Files.
2. **Connect one AI client** — same Claude / ChatGPT / Codex paths.
3. **Verify a grounded answer** — confirm a source-backed reply from visible knowledge.

## After Essentials

- **Repeatable work:** Owners should turn one repeated task into a CompanyOS Procedure. Follow [Your first Procedure](/first-procedure). Members can browse and run published Procedures.
- **Automation:** Integrations, routines, email, Records, and HTTP automation stay optional and are not part of activation.
- **Team:** Owners can invite Members once the Workspace is grounded.

## Related pages

- [Getting Started](/getting-started)
- [Knowledge](/knowledge)
- [AI Clients](/ai-clients)
- [Your first Procedure](/first-procedure)
