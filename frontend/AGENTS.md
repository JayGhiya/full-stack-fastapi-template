<!-- UNOPLAT_CODE_CONFLUENCE_CONTEXT:BEGIN -->
<CRITICAL_INSTRUCTION>

> Generated from branch `master` at commit `1c1175eb5045e6e8fca3bcbc4134630f3ae640ba` (2026-06-12). Content may become stale as new commits land.

</CRITICAL_INSTRUCTION>

## Engineering Workflow
### Install
- `bun install` — run from the workspace root (`package.json`, `bun.lock`).

### Build
- `bun run --filter frontend build` — run from the workspace root (`package.json`, `frontend/package.json`).

### Dev
- `bun run dev` — run from the workspace root (`package.json`, `frontend/package.json`).

### Test
- `bun run test` — run from the workspace root (`package.json`, `frontend/package.json`, `frontend/playwright.config.ts`).
- `bun run test:ui` — run from the workspace root when you need Playwright UI mode (`package.json`, `frontend/package.json`, `frontend/playwright.config.ts`).

### Lint
- `bun run lint` — run from the workspace root (`package.json`, `frontend/package.json`, `frontend/biome.json`).

### Type Check
- `bunx tsc -p frontend/tsconfig.json --noEmit` — run from the workspace root (`frontend/tsconfig.json`).

## Dependency Guide
See [`dependencies_overview.md`](./dependencies_overview.md) for the full dependency catalog and usage notes.

## Business Domain
### Description
The frontend is for a generic SaaS app centered on user authentication, password recovery, and account management. It also exposes admin user management, a simple items CRUD area, and email-driven onboarding/reset flows.

### References

See [`business_domain_references.md`](./business_domain_references.md) for the supporting source references used to derive this domain summary.

## App Interfaces
See [`app_interfaces.md`](./app_interfaces.md) for the canonical interface and endpoint reference.

<!-- UNOPLAT_CODE_CONFLUENCE_CONTEXT:END -->
