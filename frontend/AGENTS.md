<!-- UNOPLAT_CODE_CONFLUENCE_CONTEXT:BEGIN -->
<CRITICAL_INSTRUCTION>

> Generated from branch `master` at commit `f6c2e534c3a04b123670119df7889ee73718235d` (2026-03-13). Content may become stale as new commits land.

</CRITICAL_INSTRUCTION>

## Engineering Workflow

| Stage | Command | Config File | Confidence |
|---|---|---|---|
| install | `npm ci` | `package.json` | 0.97 |
| build | `npm run build` | `tsconfig.build.json` | 0.97 |
| dev | `npm run dev` | `vite.config.ts` | 0.97 |
| test | `npm run test` | `playwright.config.ts` | 0.95 |
| lint | `npm run lint` | `biome.json` | 0.97 |
| type_check | `npx tsc --noEmit` | `tsconfig.json` | 0.92 |

## Dependency Guide

Full dependency purpose and usage entries are catalogued in [`dependencies_overview.md`](./dependencies_overview.md).

| Dependency | Category | One-line purpose |
|---|---|---|
| `@hookform/resolvers` | Forms | Validation resolver bridge between React Hook Form and schema libraries (Zod, Yup, etc.) |
| `@tailwindcss/vite` | Build | First-party Vite plugin for Tailwind CSS — no PostCSS config needed |
| `@tanstack/react-query` | Data fetching | Server-state management with caching, background refetch, and invalidation |
| `@tanstack/react-query-devtools` | Dev tooling | Interactive devtools panel for inspecting React Query state (dev only) |
| `@tanstack/react-router` | Routing | Type-safe, client-first React router with full TypeScript inference |
| `@tanstack/react-router-devtools` | Dev tooling | Browser devtools for TanStack Router state inspection (dev only) |
| `@tanstack/react-table` | UI | Headless, fully typed table/data-grid logic library |
| `axios` | HTTP | Promise-based isomorphic HTTP client with interceptors and TypeScript generics |
| `class-variance-authority` | Styling | Type-safe variant-driven component class management (CVA) |
| `clsx` | Styling | Tiny utility for conditional `className` string construction |
| `form-data` | HTTP | Creates `multipart/form-data` streams for file uploads |
| `lucide-react` | Icons | Tree-shakeable Lucide icon components for React |
| `next-themes` | Theming | Dark/light/system theme management with FOUC prevention |
| `Radix UI React Primitives` | UI | Unstyled, WAI-ARIA-compliant accessible component primitives |
| `react` | Core | Core React library for building component-based UIs |
| `react-dom` | Core | DOM renderer and mounting APIs for React web apps |
| `react-error-boundary` | Error handling | Reusable error boundary component and `useErrorBoundary` hook |
| `react-hook-form` | Forms | Performant form state, validation, and submission with minimal re-renders |
| `react-icons` | Icons | Large collection of popular icon packs as tree-shakeable React components |
| `sonner` | UI | Lightweight, accessible toast notification component |
| `tailwind-merge` | Styling | Merges Tailwind classes without conflicts via `twMerge` |
| `tailwindcss` | Styling | Utility-first CSS framework for rapid UI development |
| `zod` | Validation | TypeScript-first schema validation with static type inference |

## Business Logic Domain

This frontend is a full-stack web application template centred on **user identity and access management** plus a generic **Items** resource. It communicates with a FastAPI backend via an auto-generated OpenAPI client.

### Core Domains

| Domain | Summary |
|---|---|
| **Auth & Identity** | User registration, login, password recovery/reset, and profile self-management. Role distinctions: regular users, superusers, and verified accounts. |
| **Items (CRUD)** | Users can create, read, update, and delete Items scoped to their own ownership. |
| **API Transport** | Auto-generated OpenAPI client handles authentication tokens, HTTP validation errors, and cancellable API requests. |
| **Admin & Settings** | Admin panel for superuser operations; user settings views for self-service profile changes. |
| **Email Utility** | Helper for testing transactional mail delivery (used in end-to-end tests). |

### Key Data-Model & Infrastructure Files

Full annotated details are in [`business_logic_references.md`](./business_logic_references.md).

| File | Role |
|---|---|
| `src/client/types.gen.ts` | Auto-generated TypeScript types for all API request/response shapes (single source of truth for domain models). |
| `src/client/core/ApiRequestOptions.ts` | Defines the options shape passed to every outbound API call (method, URL, headers, body, etc.). |
| `src/client/core/ApiResult.ts` | Represents a completed HTTP response — status code, body, and success flag. |
| `src/client/core/CancelablePromise.ts` | Wraps Promises with abort/cancel support so in-flight requests can be cleanly abandoned. |
| `src/client/core/OpenAPI.ts` | Holds global OpenAPI client configuration: base URL, auth token resolver, and default headers. |
| `src/routeTree.gen.ts` | Auto-generated TanStack Router route tree — enumerates every frontend page/view and their nested layout relationships. |
| `tests/utils/mailcatcher.ts` | Test utility that queries a local Mailcatcher instance to assert transactional email delivery. |

## App Interfaces

No inbound, outbound, or internal interface constructs were detected for this codebase. Full interface inventory is catalogued in [`app_interfaces.md`](./app_interfaces.md).

<!-- UNOPLAT_CODE_CONFLUENCE_CONTEXT:END -->
