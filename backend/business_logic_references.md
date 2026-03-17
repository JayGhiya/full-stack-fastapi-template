# Business Logic References

## Domain Overview

This backend implements a full-stack web application centered on **user account management and item ownership**. It serves as a production-ready, multi-user SaaS-style template where identity management, role-based access control, and basic resource (item) CRUD are the primary business concerns.

---

## Core Domain Entities

### User (`app/models.py`)

The central identity entity. Authenticated users may hold a **superuser/admin role** and carry an **active/inactive state**. Passwords are stored as bcrypt hashes.

| Model Class | Purpose |
|---|---|
| `UserBase` | Shared fields: `email` (unique, indexed), `is_active`, `is_superuser`, `full_name` |
| `User` | DB table; adds `id` (UUID PK), `hashed_password`, `created_at`, and a cascade-delete `items` relationship |
| `UserCreate` | API input for admin-driven user creation; includes plaintext `password` |
| `UserRegister` | Self-registration input; email, password, optional full name |
| `UserUpdate` | Admin user update; all fields optional |
| `UserUpdateMe` | Authenticated user self-update; `full_name` and `email` only |
| `UpdatePassword` | Password change flow; requires `current_password` + `new_password` |
| `UserPublic` | API response shape; exposes `id`, `email`, `is_active`, `is_superuser`, `full_name`, `created_at` |
| `UsersPublic` | Paginated list wrapper: `data: list[UserPublic]` + `count` |

### Item (`app/models.py`)

A generic owned resource linked to a `User` via a foreign key with `CASCADE` delete.

| Model Class | Purpose |
|---|---|
| `ItemBase` | Shared fields: `title` (1–255 chars), optional `description` |
| `Item` | DB table; adds `id` (UUID PK), `created_at`, `owner_id` FK → `user.id` |
| `ItemCreate` | API creation input (inherits `ItemBase`) |
| `ItemUpdate` | API update input; `title` becomes optional |
| `ItemPublic` | API response shape; exposes `id`, `title`, `description`, `owner_id`, `created_at` |
| `ItemsPublic` | Paginated list wrapper: `data: list[ItemPublic]` + `count` |

---

## Authentication & Security Models (`app/models.py`)

| Model Class | Purpose |
|---|---|
| `Token` | JWT bearer token response: `access_token` + `token_type` (`"bearer"`) |
| `TokenPayload` | Decoded JWT body; carries `sub` (user email/id) |
| `NewPassword` | Password-reset completion payload: `token` + `new_password` |
| `Message` | Generic API response envelope: `{ "message": "..." }` |

---

## Private / Internal Provisioning (`app/api/routes/private.py`)

A private router (`/private`, tagged `"private"`) exposes an internal user-creation endpoint not subject to normal registration flows.

| Item | Detail |
|---|---|
| Endpoint | `POST /private/users/` |
| Input model | `PrivateUserCreate` — `email`, `password`, `full_name`, `is_verified` (default `False`) |
| Response model | `UserPublic` |
| Behaviour | Hashes the supplied password via `get_password_hash`, inserts a `User` row directly, returns the public user representation |
| Use case | Administrative/internal provisioning; bypasses self-registration validation |

---

## Authentication Lifecycle Utilities (`app/utils.py`)

Supporting functions that implement the full authentication and notification lifecycle.

| Function | Responsibility |
|---|---|
| `generate_password_reset_token(email)` | Mints a time-limited JWT (expiry governed by `EMAIL_RESET_TOKEN_EXPIRE_HOURS`) signed with `SECRET_KEY` for password-reset flows |
| `verify_password_reset_token(token)` | Validates and decodes the reset JWT; returns the `sub` claim (email) or `None` on failure |
| `send_email(...)` | Dispatches HTML email via SMTP using `emails` library; respects TLS/SSL/auth settings from `settings` |
| `render_email_template(template_name, context)` | Renders a Jinja2 HTML template from `app/email-templates/build/` |
| `generate_reset_password_email(...)` | Builds `EmailData` for password-recovery flow; includes a tokenised reset link |
| `generate_new_account_email(...)` | Builds `EmailData` for new-account welcome notification |
| `generate_test_email(email_to)` | Builds `EmailData` for SMTP connectivity testing |

`EmailData` is a dataclass holding `html_content` and `subject`, used as a transport object between email-generation and sending functions.

---

## Relationship Summary

```
User (1) ──── (many) Item
  └─ cascade delete: removing a User removes all owned Items
```

Role-based access is enforced at the API layer via `is_superuser` and `is_active` flags on `User`. There is no separate roles table; superuser status is a boolean attribute on the user record.