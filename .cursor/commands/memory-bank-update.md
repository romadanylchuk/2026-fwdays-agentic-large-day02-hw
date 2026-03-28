# Memory bank update

Sync the project **memory bank** under `docs/` with recent code or architecture changes the user describes (or that you infer from the current task).

## Follow this workflow

1. Read `.cursor/skills/mamory-bank-update/SKILL.md` and apply its steps.
2. Start from `docs/memory/activeContext.md`, then update only the files that are **actually** affected (e.g. `progress.md`, `techContext.md`, `systemPatterns.md`, `decisionLog.md`, `docs/technical/architecture.md`).
3. If product behavior changed, align `docs/product/PRD.md` or `domain-glossary.md` when terms or flows shift.

## Rules

- **Accuracy:** if docs and code disagree, verify in the repo and fix docs or note the gap explicitly.
- **No fluff:** short, factual updates; link file paths and commands that are real in this repo (`yarn test:all`, `yarn build:packages`, etc.).
- Do **not** duplicate `AGENTS.md` verbatim; keep `docs/memory/*` as the living detail.

## Output

- List which memory-bank files you changed and a 3–5 bullet summary of what was updated.
