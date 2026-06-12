<!-- UNOPLAT_CODE_CONFLUENCE_CONTEXT:BEGIN -->
<CRITICAL_INSTRUCTION>

> Generated from branch `master` at commit `1c1175eb5045e6e8fca3bcbc4134630f3ae640ba` (2026-06-12). Content may become stale as new commits land.

</CRITICAL_INSTRUCTION>

## Engineering Workflow
### Install
- `python -m pip install -e .` (run from `backend/`; config: `pyproject.toml`)

### Build
- Not detected.

### Dev
- `fastapi run --reload app/main.py` (run from `backend/`; config: `README.md`)

### Test
- `bash scripts/test.sh` (run from `backend/`; config: `scripts/test.sh`)
- `bash scripts/tests-start.sh` (run from `backend/`; config: `scripts/tests-start.sh`)

### Lint
- `bash scripts/lint.sh` (run from `backend/`; config: `scripts/lint.sh`)

### Type Check
- `mypy app` (run from `backend/`; config: `pyproject.toml`)
- `ty check app` (run from `backend/`; config: `pyproject.toml`)

## Dependency Guide
See [`dependencies_overview.md`](./dependencies_overview.md) for the full dependency catalog and usage notes.

## Business Domain
### Description
This backend is a general-purpose FastAPI application template centered on authenticated user management and a simple owned-item CRUD workflow. It includes email-based account onboarding, password recovery/reset, and admin/superuser controls for managing users and their items.

### References

See [`business_domain_references.md`](./business_domain_references.md) for the supporting source references used to derive this domain summary.

## App Interfaces
See [`app_interfaces.md`](./app_interfaces.md) for the canonical interface and endpoint reference.

<!-- UNOPLAT_CODE_CONFLUENCE_CONTEXT:END -->
