# Review code

You are doing a **focused code review** for this Excalidraw monorepo. Use the user’s selection, open files, or the area they describe.

## Before you conclude

1. Read **relevant** project rules under `.cursor/rules/` (especially `security.mdc`, `package-boundaries.mdc` for `packages/*`, `architecture.mdc`, `testing.mdc` for tests).
2. Prefer **facts from the diff/code** over generic advice.

## Review checklist

### Correctness & API

- Does the change match existing patterns in the same package (`packages/excalidraw`, `excalidraw-app`, etc.)?
- Types: no unnecessary `any`; public APIs stay stable unless intentionally versioned.

### Security (`security.mdc`, `security-data-restore.mdc` / `security-excalidraw-app.mdc` when applicable)

- No unsafe HTML/SVG/script vectors; no `dangerouslySetInnerHTML` for untrusted content without a reviewed sanitization path.
- URLs/navigation: reject dangerous schemes; `rel="noopener noreferrer"` for `target="_blank"` where relevant.
- Scene/import JSON: validate structure; do not execute embedded code.

### Package boundaries

- Imports respect the layer order: `common` → `math` → `element` → `excalidraw` (see `package-boundaries.mdc`). Flag upward or circular coupling.

### Performance & UX

- Avoid obvious unnecessary re-renders or hot-path work in the render loop; match how similar code is written nearby.

### Tests

- If behavior changed or new logic is non-trivial, tests should exist or be called out as a gap (`testing.mdc`).

## Output format

1. **Summary** — 2–4 bullets: what changed and overall risk.
2. **Findings** — grouped by **severity** (Blocker / Important / Nit). Each item: file (or symbol), issue, **concrete** fix or follow-up.
3. **What looks good** — brief, specific positives.
4. **Suggested next steps** — ordered list (e.g. add test, run `yarn test:typecheck`).

Do **not** rewrite large sections unless the user asked; prioritize review feedback.
