# Create component

Create or scaffold a **React component** that fits this monorepo. Infer details from the user message; ask **one** clarifying question only if the target location is ambiguous.

## Decide the home

| Goal | Typical location |
|------|------------------|
| Editor UI, canvas-adjacent UI, shared editor pieces | `packages/excalidraw/` (library) |
| App shell, collab, routing, app-only chrome | `excalidraw-app/` |
| Small example / integration demo | `examples/` (follow existing examples) |

## Conventions

- **TypeScript + React** (see `packages/tsconfig.base.json`, existing components nearby).
- **Imports:** use `@excalidraw/*` aliases as in sibling files; respect **package boundaries** (`package-boundaries.mdc`).
- **Styling:** if SCSS is used in that area, follow `styling.mdc` and match co-located `.scss` patterns.
- **State:** editor uses Jotai patterns in the package; app shell uses `excalidraw-app` + `app-jotai` — mirror nearby code.
- **Security:** no unsafe HTML; treat external/pasted content per `security.mdc`.

## Deliverables

1. **Files to add or change** — list paths.
2. **Implementation** — full code for new/changed files, matching naming and export style of the directory.
3. **Exports** — wire public exports only if this is part of the library’s public surface (follow existing `index` / barrel patterns).
4. **Tests** — if the component has logic worth testing, add or extend a `*.test.*` / `*.spec.*` next to patterns in that package (`testing.mdc`).
5. **Verify** — suggest `yarn test:typecheck` and relevant tests; use `yarn build` or `yarn build:packages` if the change touches package builds.

Keep the scope minimal: only what’s needed for the component and its integration.
