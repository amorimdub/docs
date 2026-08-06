# Build with CompanyOS

This section is for developers and automation authors who want to integrate with the CompanyOS Action Platform.

## Generated references

The reference pages below are generated from the operation contract. They stay in sync with the deployed API through the contract generator pipeline.

- [OpenAPI reference](/build-with-companyos/openapi)
- [AI-Actionable Error Catalog](/build-with-companyos/error-catalog)

## What the Action Platform covers

The Action Platform exposes operations for knowledge access, Procedure authoring, Automation Grants, Operation Approvals, the Workspace Record Store, curated Integration operations, and capability discovery. Each operation has a stable identifier, deprecation metadata, and role-based availability.

For behavior changes, follow the deprecation windows published in capability discovery.

## Ordinary HTTP, no SDK

CompanyOS publishes examples, not language SDKs. Use curl, Python, or TypeScript against `/api/v1/operations` and `/api/v1/operations/{operation_id}`.

User-facing automation guides with copy-paste examples:

- [Workspace Record Store](/record-store)
- [Managed Integrations](/managed-integrations)
- [Automation](/automation)
