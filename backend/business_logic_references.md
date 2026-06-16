# Business Logic References

Detailed reference for all domain models and supporting utilities in the backend.

---

## Domain Overview

This backend implements a **user account management and item ownership** platform. Core concerns are:

- **User lifecycle** — registration (public `UserRegister`), admin creation (`UserCreate` / private route `PrivateUserCreate`), profile update (`UserUpdateMe`), password change (`UpdatePassword`), and password reset via email token (`NewPassword`).
- **Authentication** — JWT bearer tokens (`Token`, `TokenPayload`), password hashing via `pwdlib`, and configurable token expiry.
- **Role-based access control** — `is_active` and `is_superuser` flags on every `User` record.
- **Item ownership** — `Item` entities (UUID PK, title, optional description, UTC timestamp) are owned by a `User` via a foreign-key relationship with `CASCADE DELETE`.
- **Email notifications** — Jinja2-rendered HTML emails dispatched over SMTP for password recovery, new account welcome, and test scenarios.

---

## File Reference

### `app/models.py`

Central definition of all SQLModel tables and Pydantic transfer schemas.

| Class | Kind | Purpose |
|---|---|---|
| `UserBase` | Shared base | Common user fields: `email` (unique, indexed), `is_active`, `is_superuser`, `full_name` |
| `UserCreate` | Input schema | Admin-facing creation payload; includes `password` (8–128 chars) |
| `UserRegister` | Input schema | Public self-registration payload (email, password, optional full name) |
| `UserUpdate` | Input schema | Admin-facing full update; all fields optional |
| `UserUpdateMe` | Input schema | User self-update; only `full_name` and `email` |
| `UpdatePassword` | Input schema | Secure password change; requires `current_password` and `new_password` |
| `User` | ORM table | Persisted user record; UUID PK, `hashed_password`, UTC `created_at`, cascade-delete relationship to `items` |
| `UserPublic` | Output schema | Public-safe user representation; exposes `id` and `created_at` |
| `UsersPublic` | Output schema | Paginated list wrapper: `data: list[UserPublic]`, `count: int` |
| `ItemBase` | Shared base | Common item fields: `title` (1–255 chars), optional `description` |
| `ItemCreate` | Input schema | Item creation payload (inherits `ItemBase`) |
| `ItemUpdate` | Input schema | Item update payload; `title` made optional |
| `Item` | ORM table | Persisted item record; UUID PK, UTC `created_at`, `owner_id` FK → `user.id` (CASCADE), back-populates `owner` |
| `ItemPublic` | Output schema | Public item representation; exposes `id`, `owner_id`, `created_at` |
| `ItemsPublic` | Output schema | Paginated list wrapper: `data: list[ItemPublic]`, `count: int` |
| `Message` | Utility schema | Generic `{"message": str}` API response |
| `Token` | Auth schema | Access token response: `access_token`, `token_type = "bearer"` |
| `TokenPayload` | Auth schema | JWT claims container: `sub` (subject / user email or ID) |
| `NewPassword` | Input schema | Password-reset completion: `token` (JWT) + `new_password` |

---

### `app/api/routes/private.py`

Admin-only private API route (`POST /private/users/`).

| Symbol | Kind | Purpose |
|---|---|---|
| `PrivateUserCreate` | Input schema | Pydantic model for admin direct-create: `email`, `password`, `full_name`, `is_verified` flag (default `False`) |
| `create_user` | Route handler | Hashes the supplied password with `get_password_hash`, constructs a `User` ORM instance, commits to DB, and returns `UserPublic`. Bypasses the public registration validation flow. |

---

### `app/utils.py`

Utility functions for email dispatch and password-reset token management.

| Symbol | Kind | Purpose |
|---|---|---|
| `EmailData` | Dataclass | Container for rendered email: `html_content` and `subject` |
| `render_email_template` | Function | Reads a Jinja2 HTML template from `app/email-templates/build/` and renders it with a context dict |
| `send_email` | Function | Composes and dispatches an email via the `emails` library using SMTP settings from `app.core.config.settings`; supports TLS/SSL |
| `generate_test_email` | Function | Builds an `EmailData` for a test message to a given address |
| `generate_reset_password_email` | Function | Builds an `EmailData` with a signed password-reset link (token embedded in frontend URL) |
| `generate_new_account_email` | Function | Builds an `EmailData` for a new-account welcome message including credentials |
| `generate_password_reset_token` | Function | Issues a short-lived JWT (`exp`, `nbf`, `sub=email`) signed with `SECRET_KEY` for password reset |
| `verify_password_reset_token` | Function | Decodes and validates the password-reset JWT; returns the email subject or `None` on failure |