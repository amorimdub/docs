# Permissions

CompanyOS permissions are based on Workspace membership and role.

## Roles

- **Owner**: Can manage Workspace-wide files, CompanyOS Procedures, workspace settings, and workspace-level Integrations. Only Owners can invite or grant Owner roles, and only Owners can perform owner-only destructive actions.
- **Member**: Can access visible knowledge, add Personal Files, connect Member-Scoped Integrations, and run published Procedures.

Owners include all Member capabilities.

## Workspace scoping

Every Workspace-owned query is scoped by Workspace on the server. Resource IDs supplied by a client are never used as authorization.

## Preserving ownership

CompanyOS preserves at least one Owner in every Workspace. The last Owner cannot be removed or demoted.

## Restrictions

Account status, active Workspace, role, ownership, lifecycle state, and Restrictions are resolved before every protected read or mutation.
