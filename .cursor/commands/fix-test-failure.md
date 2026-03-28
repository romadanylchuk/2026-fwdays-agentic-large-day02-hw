# Fix test failure

Debug and fix a **failing Vitest** test in this repo. Use the failure output, stack trace, or file the user points to.

## Rules (see `.cursor/rules/testing.mdc`)

- **Snapshots:** update only when the new output is **correct by design**. Use `yarn test:update` from the repo root after intentional snapshot changes — do not commit noisy snapshot churn.
- **Aliases:** keep `@excalidraw/*` imports consistent with `vitest.config.mts` (same as app code).
- **Coverage:** do not lower `coverage.thresholds` in `vitest.config.mts` without explicit justification.
- Prefer fixing **code or test expectations** over disabling suites; if you skip, document why.

## Workflow

1. **Reproduce** — identify the test file and command (e.g. `yarn test` or scoped vitest); run from repository root on Windows.
2. **Classify** — regression in product code, wrong assertion, flaky async/timer, env/jsdom/canvas mock, or snapshot drift.
3. **Fix** — minimal change; match matchers and helpers from `setupTests.ts` and sibling tests.
4. **Verify** — run the smallest command that proves the fix (single file or pattern if available).

## Output

- Root cause (1–3 sentences).
- Files changed.
- Commands run and result.
- If snapshots changed: confirm the behavioral change is intentional.
