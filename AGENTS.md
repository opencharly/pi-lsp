# AGENTS.md — pi-lsp

Vendored mirror of **pi-lsp** (npm `pi-lsp` 0.1.7; no upstream repo) for the
opencharly org. It is a declarative Pi extension for LSP diagnostics and
language-server navigation tools: users configure language servers with JSON
instead of installing a separate Pi plugin per language.

Canonical files:

- `package.json` — the npm package (`pi-lsp`, version `0.1.7`) and the
  `typecheck` / `test` / `verify` scripts.
- `extensions/pi-lsp/index.ts` — the extension entry point.
- `extensions/_shared/` — the shared config, glob, output, paths, runner,
  template, trust, and types helpers.
- `LICENSE` — upstream attribution.
- `README.md` — user overview only; never agent guidance.

There is no `charly.yml`, no candy, and no `skill:` entity — this is a vendored
mirror, so no owning `/charly-<family>:<name>` skill is projected into the
marketplace corpus.

## Load these skills first (R0)

- `/charly-internals:agents` — the closest charly skill: multi-agent support
  across harnesses and the Pi harness relationship.
- `/charly-internals:git-workflow` — before any git/PR action.

There is no pi-family owning skill in the marketplace. The gap is recorded
against `opencharly/opencharly#291`; when one is authored, add it here.

## Build / validate / test

- `npm install` — install dependencies.
- `npm run verify` — the local gate (`typecheck` + `test`); it also runs on
  `prepack`.
- `npm run typecheck` — `tsc --noEmit`.
- `npm test` — `vitest run`.
- `npm pack --dry-run` — inspect the published file set.
- This mirror carries **no `.github/workflows`**; the merge gate is the
  **org-wide** `charly/pr-validator` (required check `validate / validate`,
  defined in `opencharly/.github`).

## Modify this repo

- This is a **vendored mirror** — prefer upstreaming a fix and re-vendoring,
  rather than diverging here.
- Keep the config contract stable: global config at `~/.pi/agent/lsp.json`
  (trusted), project-local at `.pi/lsp.json` (hashed, trust-gated), project
  entries override global by `id`, and servers spawn as `bin` + `args[]`, never
  as shell strings.
- Keep `package.json`'s `version` current when re-vendoring.

## Landing

Every change lands through a pull request gated by the org-required
`charly/pr-validator`. The landing mechanics — the `feat/` branch, the PR-only
rule, `CHANGELOG/` history, and the tag-on-merge CalVer — are owned by
`/charly-internals:git-workflow` and the umbrella `AGENTS.md` /
`charly/AGENTS.md`; this signpost points at them and does not restate them.
