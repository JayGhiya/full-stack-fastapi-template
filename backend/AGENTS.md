<!-- UNOPLAT_CODE_CONFLUENCE_CONTEXT:BEGIN -->
<CRITICAL_INSTRUCTION>

> Generated from branch `master` at commit `f6c2e534c3a04b123670119df7889ee73718235d` (2026-03-17). Content may become stale as new commits land.

</CRITICAL_INSTRUCTION>

## Engineering Workflow

| Stage | Command | Config File |
|-------|---------|-------------|
| install | `uv sync --group dev` | pyproject.toml |
| dev | `uv run fastapi dev app/main.py` | pyproject.toml |
| test | `uv run coverage run -m pytest tests/ && uv run coverage report` | pyproject.toml |
| lint | `uv run ruff check app scripts --fix && uv run ruff format app scripts` | pyproject.toml |
| type_check | `uv run mypy app` | pyproject.toml |

## Dependency Guide

For a full catalog of dependencies, their purposes, and usage notes, see [dependencies_overview.md](dependencies_overview.md).

## Business Logic Domain

The backend domain covers user account management, role-based access control, and item ownership in a multi-user SaaS-style template. For full details on domain entities, authentication lifecycle, and internal provisioning, see [business_logic_references.md](business_logic_references.md).

## App Interfaces

All inbound HTTP endpoints (login, users, items, utilities, private routes) and internal SQLModel ORM relationships are catalogued in [app_interfaces.md](app_interfaces.md).

<!-- UNOPLAT_CODE_CONFLUENCE_CONTEXT:END -->
