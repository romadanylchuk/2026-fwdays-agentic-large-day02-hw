# Add Excalidraw action

Help add or extend a **user action** in the editor (menu, keyboard, history) following the existing **Action** system.

## Context (read as needed)

- `docs/memory/systemPatterns.md` — Action system overview.
- Core files: `packages/excalidraw/actions/types.ts`, `register.ts`, `manager.tsx`, `actionHistory.tsx`, `App.tsx` wiring.

## Implementation checklist

1. **Define the action** — implement `Action`: `name`, `perform`, optional `keyTest`, `PanelComponent`, `trackEvent`, `keyPriority` as in neighbors.
2. **Register** — add to the registration path used by `ActionManager.registerAll()` (see `actions/register.ts`).
3. **Keyboard** — if shortcut: implement `keyTest` without breaking existing priorities; respect `viewMode` if applicable.
4. **Undo/redo** — ensure edits go through the normal `ActionResult` / `captureUpdate` / `History` path so undo works.
5. **i18n** — if user-visible strings are added, follow existing locale patterns in the package.
6. **Tests** — add or extend tests if behavior is non-trivial (`testing.mdc`).

## Boundaries

- Keep logic in the right layer: prefer `packages/excalidraw` for editor actions; app-only wiring stays in `excalidraw-app`.
- Respect **security** for anything that touches clipboard, import, or network (`security.mdc`).

## Output

- Files changed, summary of behavior, and suggested commands: `yarn test:typecheck`, targeted tests, `yarn build:packages` if needed.
