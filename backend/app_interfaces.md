# App Interfaces

This document is the source-of-truth for all inbound HTTP endpoints and internal ORM relationships exposed by the backend.

---

## Inbound HTTP Endpoints (FastAPI)

### Authentication & Password — `app/api/routes/login.py`

| Method | Path | Notes |
|--------|------|-------|
| POST | `/login/access-token` | Issue OAuth2 access token |
| POST | `/login/test-token` | Validate token; returns `UserPublic` |
| POST | `/password-recovery/{email}` | Trigger password-recovery e-mail |
| POST | `/reset-password/` | Complete password reset with token |
| POST | `/password-recovery-html-content/{email}` | Return HTML recovery e-mail content (superuser only) |

### Users — `app/api/routes/users.py`

| Method | Path | Notes |
|--------|------|-------|
| GET | `/` | List all users (superuser only); returns `UsersPublic` |
| POST | `/` | Create user (superuser only); returns `UserPublic` |
| GET | `/me` | Current user profile; returns `UserPublic` |
| PATCH | `/me` | Update current user; returns `UserPublic` |
| PATCH | `/me/password` | Change current user password; returns `Message` |
| DELETE | `/me` | Delete own account; returns `Message` |
| POST | `/signup` | Public self-registration; returns `UserPublic` |
| GET | `/{user_id}` | Fetch user by ID; returns `UserPublic` |
| PATCH | `/{user_id}` | Update user by ID (superuser only); returns `UserPublic` |
| DELETE | `/{user_id}` | Delete user by ID (superuser only) |

### Items — `app/api/routes/items.py`

| Method | Path | Notes |
|--------|------|-------|
| GET | `/` | List items; returns `ItemsPublic` |
| GET | `/{id}` | Fetch item by ID; returns `ItemPublic` |
| POST | `/` | Create item; returns `ItemPublic` |
| PUT | `/{id}` | Replace item; returns `ItemPublic` |
| DELETE | `/{id}` | Delete item |

### Utilities — `app/api/routes/utils.py`

| Method | Path | Notes |
|--------|------|-------|
| POST | `/test-email/` | Send test e-mail (superuser only); HTTP 201 |
| GET | `/health-check/` | Liveness probe |

### Private / Internal — `app/api/routes/private.py`

| Method | Path | Notes |
|--------|------|-------|
| POST | `/users/` | Internal user creation; returns `UserPublic` |

---

## Internal Constructs — ORM Relationships (SQLModel)

Defined in `app/models.py`:

| Location | Relationship | Direction |
|----------|-------------|-----------|
| L56 | `Relationship(back_populates="owner", cascade_delete=True)` | Item → User (owner); cascade-delete items when owner is deleted |
| L96 | `Relationship(back_populates="items")` | User → Items (back-reference) |

---

## Outbound Constructs

No outbound HTTP calls or external service integrations are defined in this codebase.