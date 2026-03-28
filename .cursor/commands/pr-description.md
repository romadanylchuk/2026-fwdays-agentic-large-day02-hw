# PR description

Draft a **pull request description** for the current change (branch, diff, or summary the user provides). Target audience: reviewers in this Excalidraw monorepo.

## Include these sections

### Summary

- What problem this solves or what feature it adds (2–5 short bullets).
- Which areas are touched: `packages/*`, `excalidraw-app`, `examples`, docs, CI, etc.

### How to test

- Commands from `docs/memory/techContext.md` / `AGENTS.md`, e.g. `yarn test:typecheck`, `yarn test`, `yarn build:packages` or `yarn build` as appropriate to the diff.
- Manual checks if UI or collab behavior changed (short steps).

### Risks & notes

- **Package boundaries:** any new cross-package imports — confirm direction matches `package-boundaries.mdc`.
- **Security:** data load, URLs, HTML — note if `security.mdc` / `security-data-restore.mdc` / `security-excalidraw-app.mdc` applies.
- **Breaking changes** to public API or embed contract — call out explicitly.

### Checklist (optional)

- [ ] Tests added or updated where behavior changed
- [ ] No unintended snapshot-only churn
- [ ] Docs/memory bank updated if architecture or commands changed (`memory-bank-update` skill when relevant)

## Style

- Clear, complete sentences; avoid filler.
- Link to issues/tickets if the user provides IDs.
- Do not invent scope — if unsure, say what’s unknown or ask one focused question.
