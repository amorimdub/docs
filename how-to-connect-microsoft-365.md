# How to connect Microsoft 365

**Last verified:** 2026-08-06

Connecting Microsoft 365 lets an AI Client read your mail and calendar and, with explicit approval, send mail as you or as a Shared Mailbox. For what the sender contract guarantees, read [Email](/email). For how CompanyOS brokers connections generally, read [Managed Integrations](/managed-integrations).

Microsoft 365 is the worked example of a Nango-brokered Managed Integration. It is **Member-Scoped**: each Member connects their own organizational account, and credentials stay with that Member.

> **Admin steps on this page are not live-verified.** The CompanyOS side of this flow is implemented and described from the shipped contract. The Microsoft 365 admin-consent and Exchange Online mailbox-authority steps have not been walked end to end against a live Microsoft 365 organization — that verification is tracked as [Verify live Member and Shared Mailbox sending end to end](https://github.com/amorimdub/CompanyOS/issues/320). Treat the Microsoft-side wording below as a guide to what your admin must grant, not as a tested click path.

## Before you start

- You are signed in to CompanyOS and are a Member of the Workspace.
- You have a Microsoft 365 organizational account. Personal Microsoft accounts are not the target of this Integration.
- For Shared Mailbox sending, you need a Microsoft 365 admin. You cannot grant yourself mailbox authority.

## Part 1 — Connect your account

1. In CompanyOS, open **Integrations**.
2. Find Microsoft 365 and start connect.
3. Sign in with your Microsoft 365 organizational account and accept the consent screen.

   CompanyOS requests `Mail.Read`, `Calendars.Read`, `Mail.Send`, and delegated `Mail.Send.Shared`.
4. Confirm the Integration shows **connected** in CompanyOS.

Your Microsoft 365 organization may require an admin to approve the requested scopes before an ordinary Member can complete consent. If the sign-in stops with a message about admin approval being required, send your admin the scope list from step 3.

## Part 2 — Shared Mailbox authority (admin required)

Skip this part if you only intend to send as yourself.

`Mail.Send.Shared` does **not** by itself grant authority over any Shared Mailbox. It only permits the *pattern*. A Microsoft 365 admin must additionally grant the connected Member Exchange Online **Send As** or **Send on Behalf** permission on each specific Shared Mailbox, in the Exchange admin center or via PowerShell.

Without that grant, the Shared Mailbox will not appear as an authorized sender, and CompanyOS will not fall back to another identity to get the message out.

## Part 3 — Reconnect after a scope change

An existing token cannot gain new consent on its own. If CompanyOS adds a scope, or your admin changes what is approved, you must disconnect and reconnect the Integration — otherwise operations keep failing against the old grant.

This is also the fix when an Integration enters the **needs reconnect** state: restart connect from CompanyOS as the same Member.

## Verify

1. Ask your AI Client to discover current capabilities. Microsoft 365 operations should now appear.
2. Ask it to list authorized senders. It calls `m365_list_authorized_senders` and returns your own mailbox, plus any Shared Mailbox your admin authorized in Part 2.
3. If a Shared Mailbox is missing, the Exchange grant is the thing to check first — not the CompanyOS connection.

Never ask an AI Client to invent a From address. If a sender is not in the discovered list, it is not available.

## What CompanyOS will not do

- It does not expose a raw Microsoft Graph proxy or Nango's action catalog to an AI Client. Only curated operations are visible.
- It does not substitute another Member, another Shared Mailbox, or a CompanyOS-owned address when a sender becomes unauthorized. It fails closed.
- It does not report a message as delivered. Microsoft Graph acceptance is reported as `accepted`.

## Troubleshooting

**Consent screen says admin approval is required.** Your Microsoft 365 organization restricts user consent. Your admin must approve the requested scopes for the CompanyOS application.

**Connected, but no Microsoft 365 operations appear.** Rediscover capabilities. If they are still absent, the connection may be in a needs-reconnect state — reconnect as the same Member.

**Shared Mailbox missing from authorized senders.** Exchange **Send As** or **Send on Behalf** has not been granted for that mailbox, or was revoked. Ask your admin, then rediscover senders.

**A send fails with a sender or approval error.** Follow the linked recovery action in the [AI-Actionable Error catalog](/build-with-companyos/error-catalog). Do not retry with a different identity.

## Related pages

- [Email](/email)
- [Managed Integrations](/managed-integrations)
- [Integrations](/integrations)
- [AI-Actionable Error catalog](/build-with-companyos/error-catalog)
