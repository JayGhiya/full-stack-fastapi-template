<!-- UNOPLAT_CODE_CONFLUENCE_CONTEXT:BEGIN -->
<CRITICAL_INSTRUCTION>

> Generated from branch `master` at commit `1c1175eb5045e6e8fca3bcbc4134630f3ae640ba` (2026-06-12). Content may become stale as new commits land.

</CRITICAL_INSTRUCTION>

## Engineering Workflow
### Install
- `uv sync --all-packages` — run from the repo root; config: `pyproject.toml` and `uv.lock`
- `uv sync` — run from `backend/`; config: `backend/pyproject.toml` and `backend/README.md`
- `uv run prek install -f` — run from `backend/` to install the local pre-commit hook; config: `.pre-commit-config.yaml` and `development.md`

### Build
- `docker compose build` — run from the repo root; config: `compose.yml`

### Dev
- `docker compose watch` — run from the repo root for backend live reload development; config: `backend/README.md` and `compose.override.yml`

### Test
- `bash ./scripts/test.sh` — run from the repo root for the full Docker Compose-backed test flow; config: `scripts/test.sh`
- `uv run bash scripts/prestart.sh` — run from `backend/`; config: `.github/workflows/test-backend.yml`
- `uv run bash scripts/tests-start.sh` — run from `backend/`; config: `.github/workflows/test-backend.yml` and `backend/scripts/tests-start.sh`

### Lint
- `uv run prek run --all-files` — run from `backend/`; config: `development.md` and `.pre-commit-config.yaml`
- `uv run ruff check app` — run from `backend/`; config: `backend/scripts/lint.sh`
- `uv run ruff format app --check` — run from `backend/`; config: `backend/scripts/lint.sh`

### Type Check
- `uv run mypy app` — run from `backend/`; config: `backend/scripts/lint.sh`
- `uv run ty check app` — run from `backend/`; config: `backend/scripts/lint.sh`

## Dependency Guide
See [`dependencies_overview.md`](./dependencies_overview.md) for the full dependency catalog and usage notes.

## Business Domain
### Description
The repository is a generic SaaS starter focused on user accounts, JWT authentication, password recovery, and admin-managed user CRUD. It also includes a simple user-owned items module plus email-based onboarding and reset workflows.

### References

See [`business_domain_references.md`](./business_domain_references.md) for the supporting source references used to derive this domain summary.

## App Interfaces
See [`app_interfaces.md`](./app_interfaces.md) for the canonical interface and endpoint reference.

<!-- UNOPLAT_CODE_CONFLUENCE_CONTEXT:END -->
