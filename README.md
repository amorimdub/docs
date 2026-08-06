# CompanyOS Help Center

Published at [docs.companyos.cc](https://docs.companyos.cc) by Mintlify, which deploys from this repository's default branch.

## Do not edit these pages by hand

**This content is generated.** It is authored in the private `amorimdub/CompanyOS` repository under `docs-site/`, and copied here by `scripts/sync-docs-repo.ts`. An edit made directly in this repository will be overwritten by the next sync.

To change a page, edit it in `CompanyOS/docs-site/docs/` and re-run the sync.

## Why the split

Two pages here are not written by anyone — `build-with-companyos/openapi.md` and `build-with-companyos/error-catalog.md` are generated from `docs/contracts/` inside the CompanyOS repository by `scripts/generate-docs-site.ts`. CompanyOS CI fails if they drift from the contracts they describe.

That check only works where the contracts live, so authoring stays in CompanyOS and this repository holds the published output.

## Layout

Mintlify resolves navigation paths relative to `docs.json`, which sits at this repository's root — so pages sit at the root too. In CompanyOS they live one level deeper, under `docs-site/docs/`, beside `docs-site/docs.json`. The sync script flattens that.

## Checks that run before content reaches here

In the CompanyOS repository, `bun run docs:check`:

- verifies every `docs.json` navigation entry has a backing Markdown file;
- fails on broken internal links;
- fails on drift between the generated pages and their source contracts;
- requires a parseable `**Last verified:**` date on every `how-to-*` page, and warns when one is more than 90 days old.
