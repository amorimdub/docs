# Your first Procedure

**Last verified:** 2026-07-16

This tutorial walks an Owner through creating, repairing, approving, publishing, and running one useful **CompanyOS Procedure**. Members can use the final section to run a Procedure that is already published.

Finish [Essentials](/essentials) first so your AI Client can read real Workspace knowledge while you author.

## What you are building

A **CompanyOS Procedure** is a Workspace-wide internal instruction record. It tells an AI Client how to produce a repeatable output for Members using visible knowledge and the client's own tools. It gives **input guidance** and **output rules**. It does **not** embed a tool script, execute actions on your behalf, or rewrite source files.

You will:

1. Use the seeded **System Procedure** **Create a Procedure**.
2. Declare **Required Inputs** (and fix any **Missing Requirements**).
3. Follow the **Approval Link** returned by authoring.
4. **Publish** the first time in the web UI.
5. Complete a **first run** of the published Procedure.

## Before you start

- You are an **Owner** of the Workspace (first publish is Owner-only).
- Essentials are complete: at least one readable file, one MCP Connection, and one grounded read.
- Your AI Client is connected with Owner authority so Procedure Authoring Tools are available.

## Step 1 — Start from the System Procedure

CompanyOS seeds protected **System Procedures** into every Workspace. They are published by default and cannot be archived, deleted, or edited by Members or Owners.

1. In your AI Client, open or search for the System Procedure **Create a Procedure**.
2. Follow its guidance conversationally. Tell it what repeated work you want to capture (for example, a weekly status update, interview prep brief, or launch checklist).
3. Prefer a task your team already repeats. The goal is one useful workflow, not a perfect catalog.

The System Procedure teaches the AI Client to gather requirements, shape output rules, and call Owner-only Procedure Authoring Tools such as `create_procedure_draft` and `update_procedure`.

## Step 2 — Declare Required Inputs and repair gaps

A **Required Input** is information the Procedure must have before an AI Client may produce the output. Attach **Input Source Hints** when useful (Member in chat, a CompanyOS Knowledge Tool, or a connected read-only provider).

1. Review the draft the authoring tool created.
2. List every Required Input explicitly—do not leave “implied” inputs.
3. If the draft has a **Missing Requirement**, the authoring tool returns an **AI-Actionable Error**, and the web UI shows the same gap with repair guidance.
4. Repair in either place: ask the AI Client to update the draft, or edit in the web UI, until every Required Input and the output structure are complete.

**Procedure Templates** can shape a repeated Member-facing output. Linking a template is optional for this first tutorial; you can publish a standalone Procedure.

## Step 3 — Follow the Approval Link

Each Procedure Authoring Tool call returns an **Approval Link**: a web URL into your Workspace so you can review what the AI Client touched.

1. Open the Approval Link from the tool response (it points at the draft Procedure in the CompanyOS app).
2. Read the draft as a human Owner: tone, Required Inputs, output rules, and any linked Procedure Template.
3. Confirm nothing sensitive or incorrect would reach Members on first publish.

The Approval Link is the review bridge. It does not publish by itself.

## Step 4 — First publish in the web UI

Only an Owner can perform the **first publish**. Archive and delete also stay web-UI-only. After the first publish, later Owner edits through authoring tools go live without a second approval gate.

1. From the Procedure page opened via the Approval Link, choose **Publish**.
2. Fix any remaining Missing Requirements the UI surfaces.
3. Confirm the Procedure appears as **Published Procedure Content** available to Members through the MCP Surface.

## Step 5 — First run

1. In your AI Client (or a Member's connected client), discover the published Procedure—search by name or open it from the prompts/procedures list.
2. Supply every Required Input when asked. The AI Client should refuse to produce the final output until Required Inputs are satisfied.
3. Let the client use visible Workspace knowledge and its own tools to produce the output according to the Procedure's rules.
4. Check the result once end-to-end. That **first run** is the proof the workflow is real.

### Member path: run a published Procedure

Members do not author or publish. After an Owner publishes:

1. Connect an AI Client if you have not already ([Essentials](/essentials)).
2. Ask to run the named CompanyOS Procedure, or open it from the available procedures list.
3. Provide Required Inputs and review the grounded output.

## What not to expect

- Procedures do not silently send email, mutate Integrations, or rewrite Company Files.
- System Procedures stay CompanyOS-managed; do not try to edit **Create a Procedure** or **Create a Template**.
- Optional automation (routines, Records, HTTP) is out of scope for this tutorial.

## Related pages

- [Essentials](/essentials)
- [Procedures concepts](/procedures)
- [AI Clients](/ai-clients)
- [Permissions](/permissions)
