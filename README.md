# kata-todolist-sqlite-cargo-rs-axum-rest-node-ts-astro-dsh-qwen3.8-latest

## Continuous integration

This repository currently contains documentation and scaffolding, not a runnable
application. CI lints the Markdown that exists and verifies GitHub Actions
dependency locks. It does not claim to build or test an application.

Run the same documentation check locally:

```sh
npm ci --prefix .github/docs --ignore-scripts
node .github/docs/node_modules/markdownlint-cli2/markdownlint-cli2-bin.mjs '**/*.md' '#.github/docs/node_modules/**'
```

Documentation tooling is pinned in `.github/docs/package-lock.json`. Its KaTeX
override selects the patched 0.18.2 release for GHSA-238p-pmpm-9mq7. Long prose
lines, fragment headings, unlabelled diagram fences, and table-column alignment
are allowed; the remaining Markdown lint rules apply.

After changing workflow actions, run `gh actions-lock` (official
`github/gh-actions-lock` v0.4.1) and commit `actions.lock` with the workflows.
