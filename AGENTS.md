# AGENTS.md

## Memory Bank

The `docs/` directory is the project's **memory bank** — read it before making changes.

| File | What it tells you |
|------|-------------------|
| `docs/memory/projectbrief.md` | Project scope, main artifacts, environment constraints |
| `docs/memory/activeContext.md` | Current branch / task / focus area |
| `docs/memory/progress.md` | What is already implemented, test coverage |
| `docs/memory/productContext.md` | UX goals, key user scenarios, product constraints |
| `docs/memory/techContext.md` | Stack versions, all CLI commands, Docker setup |
| `docs/memory/systemPatterns.md` | Architecture, state management, action system, conventions |
| `docs/memory/decisionLog.md` | Key architectural decisions with rationale |
| `docs/product/PRD.md` | Reverse-engineered product requirements |
| `docs/product/domain-glossary.md` | Domain terminology (Scene, Element, Action, etc.) |
| `docs/technical/architecture.md` | Detailed architecture: layers, rendering, builds, implicit behaviors |
| `docs/technical/dev-setup.md` | Developer onboarding, env vars, IDE tips |

**Start here:** `docs/memory/activeContext.md` → then the files relevant to your task.

## Cursor rules (`.cursor/rules/`)

Project rules for the AI agent live under `.cursor/rules/`. **Security:** follow `security.mdc` (repo-wide), `security-excalidraw-app.mdc` when editing `excalidraw-app/`, and `security-data-restore.mdc` when editing `packages/excalidraw/data/`. **Packages and code quality:** `package-boundaries.mdc` and `math-geometry.mdc` for `packages/*`, `testing.mdc` for `*.test.*` / `*.spec.*`, `styling.mdc` for SCSS under `packages/excalidraw/`, `excalidraw-app/`, and `examples/`. **Library and API documentation:** `context7.mdc` — use the Context7 MCP (`resolve-library-id`, `query-docs`) when the task depends on up-to-date third-party docs. Other notable rules include `architecture.mdc`, `conventions.mdc`, `do-not-touch.mdc`, and `memory-bank.mdc`.

## Project Structure

Excalidraw is a **monorepo** with a clear separation between the core library and the application:

- **`packages/excalidraw/`** — Main React component library (`@excalidraw/excalidraw`)
- **`excalidraw-app/`** — Full-featured web application wrapping the library
- **`packages/{common,math,element,utils}`** — Shared logic, geometry, element model, helpers
- **`examples/`** — Integration examples (Next.js, browser script)

For the full repository topology and package dependency graph see `docs/technical/architecture.md`.

## Development Workflow

1. **Package Development**: Work in `packages/*` for editor features
2. **App Development**: Work in `excalidraw-app/` for app-specific features
3. **Testing**: Always run `yarn test:update` before committing
4. **Type Safety**: Use `yarn test:typecheck` to verify TypeScript

## Development Commands

```bash
yarn start            # Vite dev server for excalidraw-app
yarn build            # Production build of the app
yarn build:packages   # Build common → math → element → excalidraw
yarn test:typecheck   # TypeScript type checking
yarn test:update      # Run all tests (with snapshot updates)
yarn test:all         # typecheck + eslint + prettier + tests
yarn fix              # Auto-fix formatting and linting issues
```

Full command reference: `docs/memory/techContext.md`.

## Architecture Notes

### Package System

- Uses Yarn workspaces for monorepo management
- Internal packages use path aliases (see `vitest.config.mts`)
- Build system uses esbuild for packages, Vite for the app
- TypeScript throughout with strict configuration
- Vite resolves `@excalidraw/*` to source in dev — no rebuild needed

For state management, rendering pipeline, and implicit behaviors see `docs/memory/systemPatterns.md` and `docs/technical/architecture.md`.