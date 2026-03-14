<!-- UNOPLAT_CODE_CONFLUENCE_CONTEXT:BEGIN -->
<CRITICAL_INSTRUCTION>

> Generated from branch `master` at commit `f6c2e534c3a04b123670119df7889ee73718235d` (2026-03-13). Content may become stale as new commits land.

</CRITICAL_INSTRUCTION>

## Engineering Workflow

All commands use **uv** as the package manager. Configuration is driven by `pyproject.toml`.

| Stage | Command | Notes |
|---|---|---|
| **Install** | `uv sync --group dev` | Install all dependencies including the dev group |
| **Dev** | `uv run fastapi dev app/main.py` | Start the FastAPI development server with hot-reload |
| **Test** | `uv run coverage run -m pytest tests/` | Run the full test suite with coverage instrumentation |
| **Lint** | `uv run ruff check app` | Run Ruff linter over the `app` package |
| **Type Check** | `uv run mypy app` | Run Mypy static type checks over the `app` package |

## Dependency Guide

Full dependency purpose and usage details are maintained in [`dependencies_overview.md`](./dependencies_overview.md).

| Package | Version Constraint | Role |
|---|---|---|
| `fastapi` | unconstrained | Core web framework — routing, DI, OpenAPI docs |
| `sqlmodel` | `<1.0.0` | Unified ORM/validation layer (Pydantic + SQLAlchemy) |
| `pydantic` | unconstrained | Data validation and serialization |
| `pydantic-settings` | `<3.0.0` | Environment-variable-driven settings via `BaseSettings` |
| `alembic` | `<2.0.0` | Database schema migration management |
| `psycopg` | unconstrained | PostgreSQL database adapter (async-capable) |
| `pyjwt` | `<3.0.0` | JWT encoding/decoding for authentication |
| `pwdlib` | unconstrained | Password hashing (Argon2/Bcrypt) |
| `email-validator` | `<3.0.0.0` | Email address syntax and deliverability validation |
| `emails` | `<1.0` | Composing and sending transactional email via SMTP |
| `jinja2` | `<4.0.0` | HTML/text template rendering (e.g., email templates) |
| `httpx` | `<1.0.0` | Async-capable HTTP client (used in tests and integrations) |
| `python-multipart` | `<1.0.0` | Streaming multipart/form-data parser for file uploads |
| `sentry-sdk` | unconstrained | Error reporting and performance monitoring |
| `tenacity` | `<9.0.0` | Retry logic with configurable backoff strategies |

> See [`dependencies_overview.md`](./dependencies_overview.md) for detailed purpose and usage notes on each package.

## Business Logic Domain

All model spans have been fully inspected. Here is the domain summary:

This codebase implements a full-stack web application backend centered on **user account management and item ownership**. The core domain covers user registration, authentication (JWT bearer tokens, password hashing, and password reset flows), and role-based access control (active/superuser flags). Users own Items — titled, described entities with UUID primary keys and cascading deletion — reflecting a generic content or resource management platform. Supporting models handle transactional concerns such as email notifications, secure password updates, and both public and private (admin) user creation pathways.

Full model and utility reference details are maintained in [`business_logic_references.md`](./business_logic_references.md).

| File | Responsibility |
|---|---|
| `app/models.py` | Defines all SQLModel ORM tables (`User`, `Item`) and Pydantic transfer schemas (`UserCreate`, `UserRegister`, `UserUpdate`, `UserUpdateMe`, `UpdatePassword`, `UserPublic`, `UsersPublic`, `ItemCreate`, `ItemUpdate`, `ItemPublic`, `ItemsPublic`), plus token and utility message models |
| `app/api/routes/private.py` | Admin-only private route for direct user creation (bypasses public registration flow); hashes password and persists a `User` record via `PrivateUserCreate` payload |
| `app/utils.py` | Transactional utilities: Jinja2-based email template rendering, SMTP dispatch, password-reset JWT generation/verification, and welcome/test email builders |

## App Interfaces

Full interface details are maintained in [`app_interfaces.md`](./app_interfaces.md).

### Inbound — HTTP Endpoints (FastAPI)

#### Items (`app/api/routes/items.py`)

| Method | Path | Response Model |
|--------|------|---------------|
| `GET` | `/` | `ItemsPublic` |
| `GET` | `/{id}` | `ItemPublic` |
| `POST` | `/` | `ItemPublic` |
| `PUT` | `/{id}` | `ItemPublic` |
| `DELETE` | `/{id}` | — |

#### Login / Auth (`app/api/routes/login.py`)

| Method | Path | Response Model | Notes |
|--------|------|---------------|-------|
| `POST` | `/login/access-token` | — | Issue a JWT access token |
| `POST` | `/login/test-token` | `UserPublic` | Validate a token |
| `POST` | `/password-recovery/{email}` | — | Trigger password-reset email |
| `POST` | `/reset-password/` | — | Apply a password reset |
| `POST` | `/password-recovery-html-content/{email}` | `HTMLResponse` | Requires superuser |

#### Private / Admin (`app/api/routes/private.py`)

| Method | Path | Response Model | Notes |
|--------|------|---------------|-------|
| `POST` | `/users/` | `UserPublic` | Direct admin-only user creation |

#### Users (`app/api/routes/users.py`)

| Method | Path | Response Model | Notes |
|--------|------|---------------|-------|
| `GET` | `/` | `UsersPublic` | Requires superuser |
| `POST` | `/` | `UserPublic` | Requires superuser |
| `GET` | `/me` | `UserPublic` | Current authenticated user |
| `PATCH` | `/me` | `UserPublic` | Update own profile |
| `PATCH` | `/me/password` | `Message` | Update own password |
| `DELETE` | `/me` | `Message` | Delete own account |
| `POST` | `/signup` | `UserPublic` | Public self-registration |
| `GET` | `/{user_id}` | `UserPublic` | Get user by ID |
| `PATCH` | `/{user_id}` | `UserPublic` | Requires superuser |
| `DELETE` | `/{user_id}` | — | Requires superuser |

#### Utilities (`app/api/routes/utils.py`)

| Method | Path | Notes |
|--------|------|-------|
| `POST` | `/test-email/` | Send test email; requires superuser; returns `201` |
| `GET` | `/health-check/` | Application liveness probe |

### Outbound Interfaces

None detected.

### Internal Constructs — ORM Relationships (SQLModel, `app/models.py`)

| Relationship | Declaration |
|---|---|
| `Item → User` (owner) | `Relationship(back_populates="owner", cascade_delete=True)` — L56 |
| `User → Item` (items) | `Relationship(back_populates="items")` — L96 |

> Deleting a `User` cascades to all owned `Item` records.

<!-- UNOPLAT_CODE_CONFLUENCE_CONTEXT:END -->
