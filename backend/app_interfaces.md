# App Interfaces

Full interface details for the backend application.

---

## Inbound Interfaces — HTTP Endpoints (FastAPI)

### Items (`app/api/routes/items.py`)

| Method | Path | Response Model | Notes |
|--------|------|---------------|-------|
| `GET` | `/` | `ItemsPublic` | List all items |
| `GET` | `/{id}` | `ItemPublic` | Get a single item by ID |
| `POST` | `/` | `ItemPublic` | Create a new item |
| `PUT` | `/{id}` | `ItemPublic` | Replace an item |
| `DELETE` | `/{id}` | — | Delete an item |

### Login / Auth (`app/api/routes/login.py`)

| Method | Path | Response Model | Notes |
|--------|------|---------------|-------|
| `POST` | `/login/access-token` | — | Issue a JWT access token |
| `POST` | `/login/test-token` | `UserPublic` | Validate a token |
| `POST` | `/password-recovery/{email}` | — | Trigger password-reset email |
| `POST` | `/reset-password/` | — | Apply a password reset |
| `POST` | `/password-recovery-html-content/{email}` | `HTMLResponse` | Return HTML preview of recovery email; requires superuser |

### Private / Admin (`app/api/routes/private.py`)

| Method | Path | Response Model | Notes |
|--------|------|---------------|-------|
| `POST` | `/users/` | `UserPublic` | Direct (admin-only) user creation |

### Users (`app/api/routes/users.py`)

| Method | Path | Response Model | Notes |
|--------|------|---------------|-------|
| `GET` | `/` | `UsersPublic` | List all users; requires superuser |
| `POST` | `/` | `UserPublic` | Create a user; requires superuser |
| `GET` | `/me` | `UserPublic` | Get the current authenticated user |
| `PATCH` | `/me` | `UserPublic` | Update the current user's profile |
| `PATCH` | `/me/password` | `Message` | Update the current user's password |
| `DELETE` | `/me` | `Message` | Delete the current user's own account |
| `POST` | `/signup` | `UserPublic` | Public self-registration |
| `GET` | `/{user_id}` | `UserPublic` | Get a user by ID |
| `PATCH` | `/{user_id}` | `UserPublic` | Update a user by ID; requires superuser |
| `DELETE` | `/{user_id}` | — | Delete a user by ID; requires superuser |

### Utilities (`app/api/routes/utils.py`)

| Method | Path | Response Model | Notes |
|--------|------|---------------|-------|
| `POST` | `/test-email/` | — | Send a test email; requires superuser; returns `201` |
| `GET` | `/health-check/` | — | Application liveness check |

---

## Outbound Interfaces

None detected.

---

## Internal Constructs — ORM Relationships (SQLModel)

Defined in `app/models.py`:

| Line | Relationship | Description |
|------|-------------|-------------|
| L56 | `Item → User` | `Relationship(back_populates="owner", cascade_delete=True)` — each Item holds a reference to its owning User; deleting the User cascades to its Items |
| L96 | `User → Item` | `Relationship(back_populates="items")` — each User exposes a back-populated list of owned Items |