# How search works

**Last verified:** 2026-08-13

When an AI Client calls the Knowledge `search` tool, CompanyOS does not run a single index. It gathers several views of the files visible to the caller, fuses them, then applies a configured rerank model. The AI Client writes the answer from the excerpts it receives. CompanyOS does not synthesize a reply.

For who can see which files, read [Knowledge](/knowledge). For the tools themselves, read [AI Clients](/ai-clients).

## What the AI Client calls

The Knowledge surface is three read-only tools:

- **search** — retrieve ranked excerpts from visible files.
- **read** — fetch one file by the id `search` returned.
- **list** — enumerate visible Company Files and the caller’s Personal Files.

`read` and `list` load files. `search` is the ranking path described below.

## The five lists

Search runs these lists in parallel, each already limited to the caller’s Workspace and Personal Files:

1. **Chunk full text** — lexical match on passage text.
2. **Chunk embeddings** — nearest-neighbor match on stored passage vectors.
3. **Title and path** — lexical match on titles, folders, and heading paths.
4. **Distilled Summary full text** — lexical match on the document-level abstract, when one exists.
5. **Distilled Summary embeddings** — vector match on that abstract, when one exists.

A Distilled Summary is a retrieval aid. It never gates a file becoming readable, and it is never the cited artifact. Citations point at the Document Version.

If embeddings or summaries are unavailable for a query, search continues on the lists that still returned hits and marks the result as degraded. Catalog or authorization failure fails closed: no partial out-of-scope hits.

## Rank, then rerank

The lists are fused with Reciprocal Rank Fusion so a file that only won on meaning still competes with a file that only matched the words. A deterministic pass then applies light freshness and metadata boosts.

A configured rerank model then scores the fused candidates against the question and reorders the excerpts returned to the AI Client. If that model is unset or fails, search keeps the fused order.

## What this is not

- CompanyOS does not train on Workspace files.
- Search does not include another Member’s Personal Files.
- AI Clients cannot edit or delete source files through these tools.
