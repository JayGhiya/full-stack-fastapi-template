# Business Logic References

## Domain Overview

This frontend application is a full-stack user and item management platform built on top of a FastAPI backend. It handles user authentication flows — including login, registration, password recovery, and reset — alongside role-based access control (standard users vs. superusers). Users can manage their own profiles and passwords, while admins have a dedicated panel to create, read, update, and delete other user accounts. The application also supports CRUD operations on user-owned "items," each with a title and optional description, surfaced through dedicated routes for items, settings, and admin management.

## Data Models & Key Source Files

| File | Role |
|---|---|
| `src/client/types.gen.ts` | Auto-generated TypeScript types that mirror the FastAPI backend schemas (users, items, auth payloads, etc.). Central source of truth for all domain shapes consumed by the UI. |
| `src/client/core/ApiRequestOptions.ts` | Defines the shape of every outgoing HTTP request (method, URL, headers, body, query parameters). |
| `src/client/core/ApiResult.ts` | Defines the shape of every HTTP response (status code, status text, body). |
| `src/client/core/CancelablePromise.ts` | Provides a cancellable Promise wrapper used by all API client calls to support request abortion. |
| `src/client/core/OpenAPI.ts` | Holds the global OpenAPI configuration (base URL, token resolver, headers) used by the generated API client. |
| `src/routeTree.gen.ts` | Auto-generated TanStack Router route tree that maps URL paths to page components (login, register, items, settings, admin, etc.). |
| `tests/utils/mailcatcher.ts` | Test utility for inspecting emails sent during auth flows (password recovery, registration confirmation) via the MailCatcher service. |

## Functional Areas

### Authentication & Session Management
- Login with username/password; JWT token stored and attached to subsequent requests via `OpenAPI.ts`.
- Password recovery (request reset email) and password reset (submit new password via token link).
- New user registration flow.

### Role-Based Access Control
- **Standard users**: can view and edit their own profile and password, and manage their own items.
- **Superusers (admins)**: have access to the admin panel to create, read, update, and delete any user account.

### User Profile Management
- Users can update their display name, email, and password through a dedicated settings route.

### Item Management (CRUD)
- Authenticated users can create, read, update, and delete "items" (each with a `title` and an optional `description`).
- Items are scoped to the owning user.

### Admin Panel
- Superusers access a dedicated route to list all users and perform full CRUD on user accounts.

## Route Structure (from `routeTree.gen.ts`)

| Route Pattern | Purpose |
|---|---|
| `/login` | Login page |
| `/signup` | New user registration |
| `/recover-password` | Request password-reset email |
| `/reset-password` | Submit new password via reset token |
| `/items` | Manage own items (CRUD) |
| `/settings` | User profile & password settings |
| `/admin` | Superuser panel — user account management |