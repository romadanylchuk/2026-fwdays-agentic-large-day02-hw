# Verify build

Run verification for this repo after substantive edits. Use the **terminal** at the repository root (`d:\WebServer\Fun\anotherfork\2026-fwdays-agentic-large-day02-hw` or workspace root).

## Commands (pick based on what changed)

| Change touched | Run |
|----------------|-----|
| `packages/*` public API or build scripts | `yarn build:packages` |
| `excalidraw-app` or app build | `yarn build` |
| Any TS/types | `yarn test:typecheck` |
| Tests expected | `yarn test` or scoped vitest as in `package.json` |
| Full gate before commit | `yarn test:all` (per `AGENTS.md` / `techContext.md`) |

Also read `.cursor/skills/build-verify/SKILL.md` when the user asked for a build-only check.

## What you do

1. Run the **minimal** set that covers the change; expand if something fails.
2. Paste or summarize **relevant** error output; fix compile/type errors without `// @ts-ignore` hacks unless unavoidable and justified.
3. Report **pass/fail** and what you fixed.

If you cannot run commands, say so and list exact commands for the user.
