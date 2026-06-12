<!-- UNOPLAT_CODE_CONFLUENCE_CONTEXT:BEGIN -->
<CRITICAL_INSTRUCTION>

> Generated from branch `master` at commit `1c1175eb5045e6e8fca3bcbc4134630f3ae640ba` (2026-06-12). Content may become stale as new commits land.

</CRITICAL_INSTRUCTION>

## Engineering Workflow
### Install
- `python -m pip install -e .` — install the backend package from `pyproject.toml` (working directory: `.`; config file: `pyproject.toml`).
- `python -m pip install --group './pyproject.toml:dev'` — install the `dev` dependency group declared in `pyproject.toml` (working directory: `.`; config file: `pyproject.toml`).

### Build
- Not detected.

### Dev
- `fastapi run --reload app/main.py` — run the backend with auto-reload as described in `README.md` (working directory: `.`; config file: `README.md`).

### Test
- `bash scripts/test.sh` — run coverage, pytest, and the HTML coverage report (working directory: `.`; config file: `scripts/test.sh`).
- `bash scripts/tests-start.sh` — run the pre-start checks and then the test suite when the rest of the stack is already running (working directory: `.`; config file: `scripts/tests-start.sh`).

### Lint
- `bash scripts/format.sh` — auto-fix and format with Ruff (working directory: `.`; config file: `scripts/format.sh`).
- `bash scripts/lint.sh` — run mypy, ty, Ruff check, and Ruff format checks (working directory: `.`; config file: `scripts/lint.sh`).

### Type Check
- `mypy app` — strict mypy checks per `pyproject.toml` (working directory: `.`; config file: `pyproject.toml`).
- `ty check app` — ty checks per `pyproject.toml` (working directory: `.`; config file: `pyproject.toml`).

## Dependency Guide
See [`dependencies_overview.md`](./dependencies_overview.md) for the full dependency catalog and usage notes.

## Business Domain
### Description
FastAPI backend for user and item management with JWT-based authentication, signup/login, password recovery, and superuser controls over users and items.

### References

See [`business_domain_references.md`](./business_domain_references.md) for the supporting source references used to derive this domain summary.

## App Interfaces
See [`app_interfaces.md`](./app_interfaces.md) for the canonical interface and endpoint reference.

<!-- UNOPLAT_CODE_CONFLUENCE_CONTEXT:END -->
