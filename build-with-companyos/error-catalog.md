# AI-Actionable Error Catalog

This page is generated from `docs/contracts/ai-actionable-errors.md`.

# Action Platform AI-Actionable Error Catalog

Generated from /api/v1/operations operation contract at runtime.

<a id="error-action_platform_authentication_required"></a>
# error-action_platform_authentication_required
- code: action_platform_authentication_required
- message: Authentication is required to use the Action Platform.
- recoverable: true
- next: Sign in to CompanyOS or provide a valid Automation Grant or operation approval.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-action_platform_authentication_required
- sources: action-platform

<a id="error-action_platform_unavailable"></a>
# error-action_platform_unavailable
- code: action_platform_unavailable
- message: The Action Platform is unavailable right now.
- recoverable: true
- next: Retry the operation shortly.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-action_platform_unavailable
- sources: action-platform

<a id="error-action_platform_workspace_access_required"></a>
# error-action_platform_workspace_access_required
- code: action_platform_workspace_access_required
- message: An active Workspace membership is required to use the Action Platform.
- recoverable: true
- next: Select an active Workspace where you are a Member and retry.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-action_platform_workspace_access_required
- sources: action-platform

<a id="error-automation_grant_creation_failed"></a>
# error-automation_grant_creation_failed
- code: automation_grant_creation_failed
- message: Could not create the Automation Grant.
- recoverable: true
- next: Check the requested operation scope and retry.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-automation_grant_creation_failed
- sources: action-platform

<a id="error-automation_grant_expired"></a>
# error-automation_grant_expired
- code: automation_grant_expired
- message: Automation Grant has expired.
- recoverable: true
- next: Issue a new grant before retrying this operation.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-automation_grant_expired
- sources: action-platform

<a id="error-automation_grant_membership_removed"></a>
# error-automation_grant_membership_removed
- code: automation_grant_membership_removed
- message: The grant no longer has workspace access.
- recoverable: true
- next: Recreate this grant from an active workspace membership.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-automation_grant_membership_removed
- sources: action-platform

<a id="error-automation_grant_not_found"></a>
# error-automation_grant_not_found
- code: automation_grant_not_found
- message: Automation Grant is invalid.
- recoverable: true
- next: Issue a new grant and use its latest secret.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-automation_grant_not_found
- sources: action-platform

<a id="error-automation_grant_operation_scope_mismatch"></a>
# error-automation_grant_operation_scope_mismatch
- code: automation_grant_operation_scope_mismatch
- message: Automation Grant does not authorize this operation.
- recoverable: false
- next: Use a grant issued for this operation.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-automation_grant_operation_scope_mismatch
- sources: action-platform

<a id="error-automation_grant_operation_unavailable"></a>
# error-automation_grant_operation_unavailable
- code: automation_grant_operation_unavailable
- message: The requested operation is not currently available.
- recoverable: true
- next: Use capability discovery to select an available operation.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-automation_grant_operation_unavailable
- sources: action-platform

<a id="error-automation_grant_revoked"></a>
# error-automation_grant_revoked
- code: automation_grant_revoked
- message: Automation Grant has been revoked.
- recoverable: true
- next: Issue a new grant before retrying this operation.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-automation_grant_revoked
- sources: action-platform

<a id="error-invalid_input"></a>
# error-invalid_input
- code: invalid_input
- message: The request input is invalid.
- recoverable: true
- next: Use one of the documented input values and retry.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-invalid_input
- sources: knowledge.list_visible_files, procedures.create_draft, record_store.create_collection, record_store.push_record, record_store.get_record, record_store.list_records, record_store.replace_record, record_store.patch_record, record_store.get_record_history, record_store.archive_record, record_store.restore_record, record_store.permanently_delete_record, record_store.archive_collection, record_store.restore_collection, record_store.permanently_delete_collection, m365.list_authorized_senders, m365.list_send_history, m365.send_email

<a id="error-knowledge_unavailable"></a>
# error-knowledge_unavailable
- code: knowledge_unavailable
- message: Visible files cannot be listed right now.
- recoverable: true
- next: Retry the operation shortly.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-knowledge_unavailable
- sources: knowledge.list_visible_files

<a id="error-m365_action_log_unavailable"></a>
# error-m365_action_log_unavailable
- code: m365_action_log_unavailable
- message: Microsoft 365 send history is temporarily unavailable.
- recoverable: true
- next: Retry shortly. If history remains unavailable, contact Workspace support.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-m365_action_log_unavailable
- sources: action-platform

<a id="error-m365_connection_needs_reconnect"></a>
# error-m365_connection_needs_reconnect
- code: m365_connection_needs_reconnect
- message: Microsoft 365 connection needs reconnect before mail can be sent or discovered.
- recoverable: true
- next: Ask the Member to reconnect Microsoft 365 in CompanyOS, then retry.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-m365_connection_needs_reconnect
- sources: action-platform

<a id="error-m365_connection_required"></a>
# error-m365_connection_required
- code: m365_connection_required
- message: Microsoft 365 is not connected for this Member.
- recoverable: true
- next: Ask the Member to connect Microsoft 365 in CompanyOS, then retry.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-m365_connection_required
- sources: action-platform

<a id="error-m365_no_available_sender"></a>
# error-m365_no_available_sender
- code: m365_no_available_sender
- message: No authorized Microsoft 365 sender is available for this Member.
- recoverable: true
- next: Connect Microsoft 365 for this Member, or configure an authorized Shared Mailbox, then retry discovery.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-m365_no_available_sender
- sources: action-platform

<a id="error-m365_provider_failure"></a>
# error-m365_provider_failure
- code: m365_provider_failure
- message: Microsoft 365 could not accept the email submission.
- recoverable: true
- next: Retry shortly. If the failure persists, ask the Member to reconnect Microsoft 365.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-m365_provider_failure
- sources: action-platform

<a id="error-m365_routine_grant_cadence_exceeded"></a>
# error-m365_routine_grant_cadence_exceeded
- code: m365_routine_grant_cadence_exceeded
- message: This scheduled send exceeds the maximum cadence allowed by the Routine Grant.
- recoverable: true
- next: Wait until the grant's maximum cadence elapses, or issue a new grant with a higher cadence if authorized.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-m365_routine_grant_cadence_exceeded
- sources: action-platform

<a id="error-m365_routine_grant_mismatch"></a>
# error-m365_routine_grant_mismatch
- code: m365_routine_grant_mismatch
- message: The scheduled send does not match the Routine Grant binding.
- recoverable: false
- next: Use the exact Shared Mailbox sender and recipients recorded on the Routine Grant. Issue a new grant to change them.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-m365_routine_grant_mismatch
- sources: action-platform

<a id="error-m365_routine_grant_required"></a>
# error-m365_routine_grant_required
- code: m365_routine_grant_required
- message: Scheduled Microsoft 365 sends require a Routine Grant that binds an exact Shared Mailbox, recipients, and output definition.
- recoverable: true
- next: Issue a Routine Grant for m365.send_email with sender_id, to, cc, output_definition, max cadence, and expiry, then retry with that grant.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-m365_routine_grant_required
- sources: action-platform

<a id="error-m365_sender_not_authorized"></a>
# error-m365_sender_not_authorized
- code: m365_sender_not_authorized
- message: sender_id is not an authorized sender for this Member connection.
- recoverable: true
- next: Call m365.list_authorized_senders and use a returned sender_id. Never invent a From address.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-m365_sender_not_authorized
- sources: action-platform

<a id="error-m365_sender_permission_lost"></a>
# error-m365_sender_permission_lost
- code: m365_sender_permission_lost
- message: Authority to use the selected Microsoft 365 sender was lost.
- recoverable: true
- next: Re-discover authorized senders and repair Shared Mailbox or Member mailbox permissions, then prepare a new approval or grant.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-m365_sender_permission_lost
- sources: action-platform

<a id="error-m365_sender_required"></a>
# error-m365_sender_required
- code: m365_sender_required
- message: Scheduled Microsoft 365 sends require an exact discovered sender_id.
- recoverable: true
- next: Bind a discovered sender_id in the Routine Grant and retry the scheduled invocation.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-m365_sender_required
- sources: action-platform

<a id="error-m365_sender_unavailable"></a>
# error-m365_sender_unavailable
- code: m365_sender_unavailable
- message: The selected Microsoft 365 sender is currently unavailable.
- recoverable: true
- next: Re-discover authorized senders and choose an available sender, or repair Shared Mailbox authority.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-m365_sender_unavailable
- sources: action-platform

<a id="error-m365_submission_idempotency_required"></a>
# error-m365_submission_idempotency_required
- code: m365_submission_idempotency_required
- message: Microsoft 365 email submission requires durable idempotency.
- recoverable: true
- next: Retry after CompanyOS can persist the submission, using the issued approval or routine invocation identifier.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-m365_submission_idempotency_required
- sources: action-platform

<a id="error-m365_submission_pending"></a>
# error-m365_submission_pending
- code: m365_submission_pending
- message: This Microsoft 365 email submission is still in progress.
- recoverable: true
- next: Retry with the same idempotency key to receive the original submission outcome.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-m365_submission_pending
- sources: action-platform

<a id="error-m365_submission_unknown"></a>
# error-m365_submission_unknown
- code: m365_submission_unknown
- message: Microsoft 365 submission outcome is unknown; the message may already have been accepted.
- recoverable: true
- next: Do not send again with a new idempotency key. Retry with the same idempotency key to read the stored outcome, or inspect the mailbox Sent Items before composing a new message.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-m365_submission_unknown
- sources: action-platform

<a id="error-operation_approval_consumed"></a>
# error-operation_approval_consumed
- code: operation_approval_consumed
- message: Operation approval was already used.
- recoverable: true
- next: Issue a new approval before retrying this operation.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-operation_approval_consumed
- sources: action-platform

<a id="error-operation_approval_expired"></a>
# error-operation_approval_expired
- code: operation_approval_expired
- message: Operation approval has expired.
- recoverable: true
- next: Issue a new approval before retrying this operation.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-operation_approval_expired
- sources: action-platform

<a id="error-operation_approval_membership_removed"></a>
# error-operation_approval_membership_removed
- code: operation_approval_membership_removed
- message: The approval no longer has workspace access.
- recoverable: true
- next: Recreate the approval from an active workspace membership.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-operation_approval_membership_removed
- sources: action-platform

<a id="error-operation_approval_not_found"></a>
# error-operation_approval_not_found
- code: operation_approval_not_found
- message: Operation approval is invalid.
- recoverable: true
- next: Issue a new approval and use its latest secret.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-operation_approval_not_found
- sources: action-platform

<a id="error-operation_approval_payload_mismatch"></a>
# error-operation_approval_payload_mismatch
- code: operation_approval_payload_mismatch
- message: Execution payload does not match the prepared operation payload.
- recoverable: false
- next: Prepare a new approval with the exact operation input.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-operation_approval_payload_mismatch
- sources: action-platform

<a id="error-operation_approval_scope_mismatch"></a>
# error-operation_approval_scope_mismatch
- code: operation_approval_scope_mismatch
- message: Operation approval was issued for another operation.
- recoverable: false
- next: Use an approval issued for this operation.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-operation_approval_scope_mismatch
- sources: action-platform

<a id="error-operation_not_found"></a>
# error-operation_not_found
- code: operation_not_found
- message: The requested operation is not available.
- recoverable: false
- next: Use capability discovery to select an available operation.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-operation_not_found
- sources: action-platform

<a id="error-owner_required"></a>
# error-owner_required
- code: owner_required
- message: Owner role required to execute this operation.
- recoverable: true
- next: Ask a Workspace Owner to run this action.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-owner_required
- sources: procedures.create_draft, record_store.create_collection, record_store.permanently_delete_record, record_store.archive_collection, record_store.restore_collection, record_store.permanently_delete_collection

<a id="error-procedure_create_failed"></a>
# error-procedure_create_failed
- code: procedure_create_failed
- message: Could not create the procedure draft.
- recoverable: true
- next: Check required input and retry the write.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-procedure_create_failed
- sources: procedures.create_draft

<a id="error-procedure_write_unavailable"></a>
# error-procedure_write_unavailable
- code: procedure_write_unavailable
- message: Procedure write capability is not available for this Workspace.
- recoverable: false
- next: Enable procedure writes for this workspace and retry.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-procedure_write_unavailable
- sources: procedures.create_draft

<a id="error-record_store_collection_archived"></a>
# error-record_store_collection_archived
- code: record_store_collection_archived
- message: The Collection is archived and cannot accept new Records.
- recoverable: true
- next: Restore the Collection first, then retry the operation.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-record_store_collection_archived
- sources: record_store.push_record, record_store.replace_record, record_store.patch_record, record_store.archive_record, record_store.restore_record

<a id="error-record_store_collection_not_archived"></a>
# error-record_store_collection_not_archived
- code: record_store_collection_not_archived
- message: Only an archived Collection can be permanently deleted.
- recoverable: true
- next: Archive the Collection first, permanently delete its Records, then retry.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-record_store_collection_not_archived
- sources: record_store.permanently_delete_collection

<a id="error-record_store_collection_not_empty"></a>
# error-record_store_collection_not_empty
- code: record_store_collection_not_empty
- message: The Collection still contains Records and cannot be permanently deleted.
- recoverable: true
- next: Permanently delete every Record in the Collection, then retry.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-record_store_collection_not_empty
- sources: record_store.permanently_delete_collection

<a id="error-record_store_collection_not_found"></a>
# error-record_store_collection_not_found
- code: record_store_collection_not_found
- message: The requested Collection was not found in this Workspace.
- recoverable: true
- next: Create the Collection first, then retry the operation.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-record_store_collection_not_found
- sources: record_store.push_record, record_store.get_record, record_store.list_records, record_store.replace_record, record_store.patch_record, record_store.get_record_history, record_store.archive_record, record_store.restore_record, record_store.permanently_delete_record, record_store.archive_collection, record_store.restore_collection, record_store.permanently_delete_collection

<a id="error-record_store_idempotency_conflict"></a>
# error-record_store_idempotency_conflict
- code: record_store_idempotency_conflict
- message: The provided idempotency key has already been used with a different payload.
- recoverable: true
- next: Use the original payload to retry, or generate a new idempotency key.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-record_store_idempotency_conflict
- sources: record_store.push_record

<a id="error-record_store_invalid_payload"></a>
# error-record_store_invalid_payload
- code: record_store_invalid_payload
- message: The Record payload must be a valid JSON object.
- recoverable: true
- next: Retry with a JSON object. Arrays, primitives, and binary values are not accepted.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-record_store_invalid_payload
- sources: record_store.push_record, record_store.replace_record, record_store.patch_record

<a id="error-record_store_operation_failed"></a>
# error-record_store_operation_failed
- code: record_store_operation_failed
- message: Could not complete the Record Store operation.
- recoverable: true
- next: Check the operation input and retry, or contact support if the problem persists.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-record_store_operation_failed
- sources: record_store.create_collection, record_store.push_record, record_store.get_record, record_store.list_records, record_store.replace_record, record_store.patch_record, record_store.get_record_history, record_store.archive_record, record_store.restore_record, record_store.permanently_delete_record, record_store.archive_collection, record_store.restore_collection, record_store.permanently_delete_collection

<a id="error-record_store_payload_too_large"></a>
# error-record_store_payload_too_large
- code: record_store_payload_too_large
- message: The Record payload exceeds the maximum allowed size.
- recoverable: true
- next: Reduce the payload size and retry, or contact a Workspace Owner to discuss quota options.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-record_store_payload_too_large
- sources: record_store.push_record, record_store.replace_record, record_store.patch_record

<a id="error-record_store_quota_exceeded"></a>
# error-record_store_quota_exceeded
- code: record_store_quota_exceeded
- message: The Workspace Record Store quota has been exceeded.
- recoverable: true
- next: Reduce payload size, permanently delete unneeded Records or Collections, or contact a Workspace Owner to discuss quota options.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-record_store_quota_exceeded
- sources: record_store.create_collection, record_store.push_record, record_store.replace_record, record_store.patch_record, record_store.archive_record, record_store.restore_record

<a id="error-record_store_record_not_found"></a>
# error-record_store_record_not_found
- code: record_store_record_not_found
- message: The requested Record was not found in this Collection.
- recoverable: true
- next: Check the Record identifier and retry, or list Records in the Collection.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-record_store_record_not_found
- sources: record_store.get_record, record_store.replace_record, record_store.patch_record, record_store.get_record_history, record_store.archive_record, record_store.restore_record, record_store.permanently_delete_record

<a id="error-record_store_stale_version"></a>
# error-record_store_stale_version
- code: record_store_stale_version
- message: The expected version does not match the current Record version.
- recoverable: true
- next: Fetch the current Record and retry with the latest version.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-record_store_stale_version
- sources: record_store.replace_record, record_store.patch_record, record_store.archive_record, record_store.restore_record

<a id="error-record_store_unavailable"></a>
# error-record_store_unavailable
- code: record_store_unavailable
- message: The Workspace Record Store is unavailable right now.
- recoverable: true
- next: Retry the operation shortly.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-record_store_unavailable
- sources: record_store.create_collection, record_store.push_record, record_store.get_record, record_store.list_records, record_store.replace_record, record_store.patch_record, record_store.get_record_history, record_store.archive_record, record_store.restore_record, record_store.permanently_delete_record, record_store.archive_collection, record_store.restore_collection, record_store.permanently_delete_collection

<a id="error-record_store_write_denied"></a>
# error-record_store_write_denied
- code: record_store_write_denied
- message: You do not have permission to write this Collection.
- recoverable: true
- next: Ask a Workspace Owner to enable Member writes for this Collection, or run the operation as an Owner.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-record_store_write_denied
- sources: record_store.push_record, record_store.replace_record, record_store.patch_record, record_store.archive_record, record_store.restore_record

<a id="error-routine_grant_collection_not_allowed"></a>
# error-routine_grant_collection_not_allowed
- code: routine_grant_collection_not_allowed
- message: Routine Grant does not authorize this Workspace Collection.
- recoverable: false
- next: Add the Collection to the Routine Grant data scopes, or ask a Workspace Owner to include it.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-routine_grant_collection_not_allowed
- sources: action-platform

<a id="error-routine_grant_connection_needs_reconnect"></a>
# error-routine_grant_connection_needs_reconnect
- code: routine_grant_connection_needs_reconnect
- message: A Routine Grant Integration connection needs reconnect.
- recoverable: true
- next: Reconnect the Integration in CompanyOS, then retry.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-routine_grant_connection_needs_reconnect
- sources: action-platform

<a id="error-routine_grant_connection_revoked"></a>
# error-routine_grant_connection_revoked
- code: routine_grant_connection_revoked
- message: A Routine Grant Integration connection was revoked.
- recoverable: true
- next: Reconnect the Integration in CompanyOS, then issue a new Routine Grant.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-routine_grant_connection_revoked
- sources: action-platform

<a id="error-routine_grant_creation_failed"></a>
# error-routine_grant_creation_failed
- code: routine_grant_creation_failed
- message: Could not create the Routine Grant.
- recoverable: true
- next: Check the requested operation scope, AI client type, and expiry, then retry.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-routine_grant_creation_failed
- sources: action-platform

<a id="error-routine_grant_data_scope_mismatch"></a>
# error-routine_grant_data_scope_mismatch
- code: routine_grant_data_scope_mismatch
- message: Routine Grant does not authorize this data scope.
- recoverable: false
- next: Use the Company Files scope authorized by this Routine Grant.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-routine_grant_data_scope_mismatch
- sources: action-platform

<a id="error-routine_grant_expired"></a>
# error-routine_grant_expired
- code: routine_grant_expired
- message: Routine Grant has expired.
- recoverable: true
- next: Issue a new grant before retrying this operation.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-routine_grant_expired
- sources: action-platform

<a id="error-routine_grant_integration_not_allowed"></a>
# error-routine_grant_integration_not_allowed
- code: routine_grant_integration_not_allowed
- message: Routine Grant does not authorize this Integration.
- recoverable: false
- next: Add the Integration to the Routine Grant data scopes, or reconnect it if disconnected.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-routine_grant_integration_not_allowed
- sources: action-platform

<a id="error-routine_grant_invocation_id_required"></a>
# error-routine_grant_invocation_id_required
- code: routine_grant_invocation_id_required
- message: A stable invocation ID is required for scheduled calls.
- recoverable: true
- next: Include x-routine-invocation-id with a stable caller-generated identifier and retry.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-routine_grant_invocation_id_required
- sources: action-platform

<a id="error-routine_grant_invocation_pending"></a>
# error-routine_grant_invocation_pending
- code: routine_grant_invocation_pending
- message: This Routine Grant invocation is still in progress.
- recoverable: true
- next: Retry with the same invocation ID to receive its original result.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-routine_grant_invocation_pending
- sources: action-platform

<a id="error-routine_grant_membership_removed"></a>
# error-routine_grant_membership_removed
- code: routine_grant_membership_removed
- message: The grant no longer has workspace access.
- recoverable: true
- next: Recreate this grant from an active workspace membership.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-routine_grant_membership_removed
- sources: action-platform

<a id="error-routine_grant_not_found"></a>
# error-routine_grant_not_found
- code: routine_grant_not_found
- message: Routine Grant is invalid.
- recoverable: true
- next: Issue a new grant and use its latest secret.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-routine_grant_not_found
- sources: action-platform

<a id="error-routine_grant_operation_scope_mismatch"></a>
# error-routine_grant_operation_scope_mismatch
- code: routine_grant_operation_scope_mismatch
- message: Routine Grant does not authorize this operation.
- recoverable: false
- next: Use a grant issued for this operation.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-routine_grant_operation_scope_mismatch
- sources: action-platform

<a id="error-routine_grant_operation_unavailable"></a>
# error-routine_grant_operation_unavailable
- code: routine_grant_operation_unavailable
- message: The requested operation is not currently available for Routine Grants.
- recoverable: true
- next: Use capability discovery to select an available operation.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-routine_grant_operation_unavailable
- sources: action-platform

<a id="error-routine_grant_personal_files_not_allowed"></a>
# error-routine_grant_personal_files_not_allowed
- code: routine_grant_personal_files_not_allowed
- message: Routine Grant does not authorize Personal Files.
- recoverable: false
- next: Include personal_files in the Routine Grant data scopes, or request Company Files only.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-routine_grant_personal_files_not_allowed
- sources: action-platform

<a id="error-routine_grant_revoked"></a>
# error-routine_grant_revoked
- code: routine_grant_revoked
- message: Routine Grant has been revoked.
- recoverable: true
- next: Issue a new grant before retrying this operation.
- docs_url: /docs/contracts/ai-actionable-errors.md#error-routine_grant_revoked
- sources: action-platform
