<!-- UNOPLAT_CODE_CONFLUENCE_CONTEXT:BEGIN -->
<CRITICAL_INSTRUCTION>

> Generated from branch `master` at commit `1c1175eb5045e6e8fca3bcbc4134630f3ae640ba` (2026-06-12). Content may become stale as new commits land.

</CRITICAL_INSTRUCTION>

## Engineering Workflow

### Install
- `cd backend && uv sync` — backend dependencies from `backend/README.md` and `backend/pyproject.toml`.
- `bun install` — frontend dependencies from `frontend/README.md` and `frontend/package.json`.

### Build
- `cd frontend && bun run build` — frontend production build from `frontend/package.json`.

### Dev
- `cd backend && fastapi dev app/main.py` — local backend server from `development.md`.
- `bun run dev` — frontend Vite dev server from the root `package.json`.
- `docker compose watch` — full-stack compose development loop from `development.md`.

### Test
- `cd backend && bash ./scripts/test.sh` — backend Pytest/coverage workflow from `backend/README.md`.
- `bunx playwright test` — frontend end-to-end tests from `frontend/README.md`.

### Lint
- `cd backend && bash ./scripts/lint.sh` — backend lint/format workflow from `backend/scripts/lint.sh`.
- `bun run lint` — frontend Biome lint/format workflow from `frontend/package.json`.

### Type Check
- `cd backend && uv run mypy app` — backend mypy check from `.pre-commit-config.yaml`.
- `cd backend && uv run ty check app` — backend ty check from `.pre-commit-config.yaml`.
- Not detected — no dedicated frontend type-check script; `bun run build` covers TypeScript compilation as part of the build step.

## Dependency Guide
See [`dependencies_overview.md`](./dependencies_overview.md) for the full dependency catalog and usage notes.

## Business Domain
### Description
This codebase is a full-stack SaaS starter centered on user account management, authentication, and profile administration. Its core models cover users, item ownership, JWT access/reset-password flows, and email notifications, with a small private admin endpoint for creating verified users.

### References

See [`business_domain_references.md`](./business_domain_references.md) for the supporting source references used to derive this domain summary.

## App Interfaces
See [`app_interfaces.md`](./app_interfaces.md) for the canonical interface and endpoint reference.

<!-- UNOPLAT_CODE_CONFLUENCE_CONTEXT:END -->
