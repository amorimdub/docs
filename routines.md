# Routines

Routines are repeatable workflows that a Workspace can run on a schedule or on demand. They combine Workspace knowledge with an Automation Grant so an unattended process can call allowed Action Platform operations.

## Supported hosting

Claude Cowork is the primary verified hosted-routine path. A Workspace owner confirmed the computer-off acceptance on July 16, 2026: the routine ran without a local CompanyOS process or local computer remaining online.

ChatGPT/Codex Hosted Scheduled is not currently a supported or verified hosting path. Codex CLI, the Codex app, and Claude Code can call CompanyOS from a machine or external host, but those are local or externally hosted automations—not CompanyOS-hosted schedules. Do not assume that closing a laptop leaves those processes running.

## Automation Grants

An Automation Grant lets a routine authenticate as one authorizing Member inside one Workspace and call explicitly allowed operations. A grant records its AI Client type, visible Company Files and any additional selected resources, maximum cadence, and expiry. The secret is displayed once; CompanyOS stores only its hash.

Authority is rechecked on every invocation. Removed membership, a changed role, revoked consent, a disconnected Integration, an unavailable operation, expiry, or revocation stops the call immediately. CompanyOS does not silently widen scope or switch to another identity.

## Operation Approval

Sensitive interactive operations use a one-time Operation Approval. The approval binds the acting Member, Workspace, operation, connection, normalized payload, and expiry. Mutation, cross-Member use, expiry, and replay fail closed. Operation approvals and executions are recorded with privacy-safe metadata.

Unattended operations cannot simulate an interactive approval. They require an Automation Grant whose operation-specific constraints authorize the exact call.

## Building routines

### Claude Cowork setup

1. Connect Claude to the Workspace MCP endpoint shown under **AI Clients** and complete the browser authentication flow.
2. Ask Claude to discover current capabilities before drafting the routine. Available operations depend on the Member, Workspace role, active Integrations, and grants.
3. In CompanyOS, create an Automation Grant for the authorizing Member. Select only the operations and Company Files the routine needs, set its maximum cadence and expiry, and copy the one-time secret into the hosted routine.
4. In Claude Cowork, create the scheduled task with the intended cadence and explicit instructions to use the CompanyOS operation identifiers returned by discovery.
5. Run it once interactively. Verify the returned CompanyOS invocation identifier and status in the grant history before relying on the schedule.
6. Run it again on schedule with the local computer off. Confirm the new invocation in CompanyOS.

CompanyOS owns grant, invocation, idempotency, and privacy-safe outcome evidence. Claude owns the schedule and prompt. CompanyOS does not claim a next-run time, pause state, or AI-generation history.

### Verification and recovery

- A repeated invocation identifier returns the original outcome; it does not execute the same operation twice.
- Revoke the grant in CompanyOS to stop future calls immediately.
- For `grant_expired`, `grant_revoked`, or authority errors, create or repair the narrowly scoped grant instead of retrying with wider permissions.
- For Integration reconnect errors, reconnect the exact Integration as the appropriate Member or Owner, rediscover capabilities, and retry.
- Never paste Workspace content, connection credentials, approval tokens, or grant secrets into support logs.

For scheduled Shared Mailbox output, also follow [Microsoft 365 email](/email). The grant must bind the exact Shared Mailbox sender, exact `to`/`cc` recipients, output definition, maximum cadence, no-attachments policy, and expiry.
