# How to schedule a Claude Cowork routine

**Last verified:** 2026-08-06

Claude Cowork is the primary hosted path for running CompanyOS work on a schedule without your computer staying on. This page is the click-by-click setup. For what routines are and how authority is checked, read [Routines](/routines).

**Hosted acceptance evidence:** a Workspace Owner confirmed the computer-off run on 2026-07-16 — the routine executed with no local CompanyOS process and no local machine online.

Claude Cowork is currently the only verified hosted path. ChatGPT/Codex Hosted Scheduled is not supported or verified. Claude Code can run CompanyOS automations, but only on a machine or external host you keep available — closing a laptop stops it. Do not treat Claude Code as cloud scheduling.

## Before you start

- Claude is already connected to the Workspace. If not, follow [How to connect Claude](/how-to-connect-claude) first.
- You know which CompanyOS operations the routine needs. Ask Claude to discover capabilities before you create the grant, so you scope it to what is actually used rather than guessing wide.

## Steps

1. **Discover capabilities.** In Claude, ask it to list the CompanyOS operations available to you. What is available depends on your Member role, the Workspace, active Integrations, and existing grants.
2. **Create an Automation Grant.** In CompanyOS, create a grant for yourself as the authorizing Member. Select:

   - only the operations the routine calls;
   - only the Company Files and resources it needs;
   - a maximum cadence;
   - an expiry.

   The secret is displayed **once**. CompanyOS stores only its hash — if you lose it, create a new grant rather than trying to recover it.
3. **Copy the secret into Claude Cowork**, not into a chat message, a shared document, or a support ticket.
4. **Create the scheduled task** in Claude Cowork with the cadence you want. Instruct it explicitly to use the CompanyOS operation identifiers returned by discovery in step 1, rather than describing the task in prose and hoping it picks the right tool.
5. **Run it once interactively.** Confirm the returned CompanyOS invocation identifier and its status appear in the grant history before you rely on the schedule.
6. **Run it on schedule with your computer off.** Confirm a new invocation appears in CompanyOS. This is the step that actually proves hosted execution — an interactive run does not.

## Who owns what

CompanyOS owns the grant, the invocation record, idempotency, and privacy-safe outcome evidence. Claude owns the schedule and the prompt.

CompanyOS therefore cannot tell you a next-run time, whether a schedule is paused, or what Claude generated. Check those in Claude Cowork. Do not expect the CompanyOS grant history to be a scheduler UI.

## Scheduled email output

If the routine sends mail from a Shared Mailbox, the grant must additionally bind the exact Shared Mailbox sender, the exact `to` and `cc` recipients, the output definition, the maximum cadence, the no-attachments policy, and the expiry. Scheduled sends always require an exact Shared Mailbox sender — an unattended run cannot simulate the interactive approval a personal send would use.

See [Email](/email) and [How to connect Microsoft 365](/how-to-connect-microsoft-365).

## Stopping and recovering

**To stop future runs immediately:** revoke the grant in CompanyOS. Authority is rechecked on every invocation, so revocation takes effect on the next call rather than at the next renewal.

**A run repeated itself.** It should not have. A repeated invocation identifier returns the original outcome instead of executing twice. If you see genuine duplicate side effects, the routine is generating a new identifier per attempt — fix the identifier, not the cadence.

**`grant_expired` or `grant_revoked`.** Create or repair a narrowly scoped grant. Do not respond by issuing a wider one.

**An Integration error.** Reconnect that exact Integration as the appropriate Member or Owner, rediscover capabilities, then retry.

Never paste Workspace content, connection credentials, approval tokens, or grant secrets into support logs.

## Related pages

- [Routines](/routines)
- [How to connect Claude](/how-to-connect-claude)
- [Email](/email)
- [AI-Actionable Error catalog](/build-with-companyos/error-catalog)
