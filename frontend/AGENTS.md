<!-- UNOPLAT_CODE_CONFLUENCE_CONTEXT:BEGIN -->
<CRITICAL_INSTRUCTION>

> Generated from branch `master` at commit `1c1175eb5045e6e8fca3bcbc4134630f3ae640ba` (2026-06-12). Content may become stale as new commits land.

</CRITICAL_INSTRUCTION>

## Engineering Workflow
### Install
- `bun install` — run from the workspace root (`.`); config: `package.json`.

### Build
- `bun run --filter frontend build` — run from the workspace root (`.`); config: `frontend/package.json`.

### Dev
- `bun run dev` — run from the workspace root (`.`); config: `package.json`.

### Test
- `bun run test` — run from the workspace root (`.`); config: `package.json`.
- `bun run test:ui` — run from the workspace root (`.`); config: `package.json`.

### Lint
- `bun run lint` — run from the workspace root (`.`); config: `package.json`.

### Type Check
- `bunx tsc -p tsconfig.json --noEmit` — run from the frontend root; config: `frontend/tsconfig.json`.

## Dependency Guide
See [`dependencies_overview.md`](./dependencies_overview.md) for the full dependency catalog and usage notes.

## Business Domain
### Description

This frontend is a generic admin-style application centered on user authentication, account management, and simple item CRUD workflows. The modeled data covers login/signup, password recovery, user profiles and admin controls, plus item records with ownership and timestamps.

### References

See [`business_domain_references.md`](./business_domain_references.md) for the supporting source references used to derive this domain summary.

## App Interfaces
See [`app_interfaces.md`](./app_interfaces.md) for the canonical interface and endpoint reference.

<!-- UNOPLAT_CODE_CONFLUENCE_CONTEXT:END -->
