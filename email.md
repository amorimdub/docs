# Email

CompanyOS has two separate email surfaces:

- Product lifecycle, approval, and Workspace-notification messages sent by CompanyOS.
- Customer correspondence sent through a connected Member's Microsoft 365 organization.

The Microsoft 365 sender path is implemented, but live Member, Shared Mailbox, and hosted scheduled-send acceptance is still pending GitHub issue #320 as of July 17, 2026. The states below describe the implemented contract; they are not a delivery or reliability claim.

## Lifecycle messaging

Email is keyed by membership. Messages are sent to the address associated with a Workspace membership, not to an abstract account.

## Approval links

When a Procedure Authoring Tool creates or edits draft Procedure Content, it returns an Approval Link. The link takes an Owner to the web UI to review the content and, for a draft, publish it.

## Notification preferences

Workspace Owners control Workspace-wide notification settings. Members receive only the messages their role and notification preferences allow.

## Connect Microsoft 365

Microsoft 365 is a Member-scoped Nango Integration. Each Member connects their own organizational account under **Integrations**. CompanyOS requests `Mail.Read`, `Calendars.Read`, `Mail.Send`, and delegated `Mail.Send.Shared`; reconnect after scopes change because an existing token cannot gain new consent automatically.

`Mail.Send.Shared` does not itself grant mailbox authority. A Microsoft 365 admin must also give the connected Member the appropriate Exchange Online **Send As** or **Send on Behalf** permission for each configured Shared Mailbox.

CompanyOS exposes curated Microsoft 365 operations only. It does not expose a raw Nango proxy or the provider's action catalog to an AI Client.

## Choose a sender

Call capability discovery and then `m365_list_authorized_senders`. Never invent a From address.

- **Member mailbox:** personal correspondence attributed to the connected Member. An interactive call may omit `sender_id` for backward compatibility, in which case only that Member's mailbox is selected.
- **Shared Mailbox:** Workspace-owned reports and routine output. Select the stable discovered `sender_id`. Scheduled sends always require an exact Shared Mailbox sender.

Unavailable or unauthorized senders are returned as unavailable or rejected. CompanyOS never falls back to another Member, another Shared Mailbox, or a CompanyOS-owned customer-output address.

## Interactive send

Interactive sending uses prepare, review, approve, and execute:

1. Discover the available sender and choose its stable `sender_id`.
2. Prepare one plain-text message with exact `to` and optional `cc` recipients, subject, and body.
3. Open the returned approval link and review the safe summary.
4. Approve as the same Member in the same Workspace.
5. Execute with the approval token and a durable idempotency identifier.

The approval binds sender, recipients, subject, body hash, Member, Workspace, connection, and expiry. Changing any bound value, replaying the approval, using another Member, or losing sender permission fails closed. The deprecated `confirm_send` value cannot authorize a send.

## Scheduled Shared Mailbox send

An unattended send requires an Automation Grant that binds:

- the exact Shared Mailbox `sender_id`;
- exact `to` and `cc` recipients;
- the Procedure or output definition;
- maximum cadence and expiry;
- the no-attachments policy; and
- the authorizing Member and active Microsoft 365 connection.

Each run supplies a stable invocation identifier. Concurrent or repeated identifiers return the existing submission outcome rather than submitting another message. Membership, connection, grant, or mailbox-authority changes block the send with no identity fallback.

HTML, attachments, BCC, dynamic recipients, mailing lists, bulk delivery, newsletters, and marketing sends are not available.

## Status and history

Microsoft Graph acceptance is reported as `accepted`, never `sent` or `delivered`. A known rejection is `failed`; an ambiguous provider outcome is `unknown` so an AI Client does not retry blindly and duplicate the message.

Members can inspect sender, recipients, subject, time, and state for their own mailbox sends. Owners see recipient count only for Member-mailbox activity, while authorized Shared Mailbox history includes sender, recipients, subject, approval or grant reference, time, and submission state. CompanyOS stores the body hash and version reference—not the message body—in the Action Log.

For sender, approval, grant, reconnect, or provider errors, follow the linked recovery action in the [AI-Actionable Error catalog](/build-with-companyos/error-catalog). Rediscover senders after repairing consent or Exchange authority; do not substitute a different identity.
