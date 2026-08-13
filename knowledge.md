# Knowledge

The Company Brain is the searchable knowledge layer for a Workspace. It is grounded in the files and read-only provider content that are visible to the caller.

## Company Files

Company Files are shared across a Workspace. Every Member can read them, and every AI Client connected to the Workspace can include them in answers.

## Personal Files

Personal Files are private to the Member who added them. Other Members, including Workspace Owners, cannot see or access another Member's Personal Files. AI Clients only receive the calling Member's own Personal Files.

## Folders

Folders group Company Files or Personal Files within a Workspace. They are a navigation aid, not a permission boundary.

## What AI Clients can do

- Search visible knowledge.
- Read individual files or records.
- List files and folders.

AI Clients cannot write, delete, or publish source knowledge.

## How search ranks files

Search is not a single index. CompanyOS runs full-text, embeddings, titles, and Distilled Summaries in parallel, fuses those lists, then applies a configured rerank model. The AI Client writes the answer from the excerpts. See [How search works](/how-search-works).
