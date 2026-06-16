# Dependencies Overview

> **Source-of-truth dependency catalog** for the `frontend` package (TypeScript / npm).
> Referenced by the `## Dependency Guide` section in `AGENTS.md`.

---

## @hookform/resolvers

**Purpose:** A validation resolver library for React Hook Form that allows seamless integration with any external validation library such as Yup, Zod, Joi, Vest, Ajv, and many others.

**Usage:** Provides a consistent resolver interface that bridges React Hook Form's `useForm` hook with third-party schema validation libraries, enabling declarative, schema-driven form validation. Resolvers accept a validation schema and return a standardized function that React Hook Form uses to validate field values and surface errors during form submission or field change events.

---

## @tailwindcss/vite

**Purpose:** A first-party Vite plugin that integrates Tailwind CSS directly into the Vite build pipeline, providing the most seamless way to use Tailwind CSS without requiring PostCSS configuration.

**Usage:** Registers Tailwind CSS as a native Vite plugin, enabling automatic CSS generation, hot module replacement (HMR), and file-system scanning during both development and production builds. Supports a wide range of Vite-based frameworks such as React, SvelteKit, Vue, Nuxt, SolidJS, and Laravel out of the box.

---

## @tanstack/react-query

**Purpose:** TanStack Query (FKA React Query) is often described as the missing data-fetching library for web applications — it makes fetching, caching, synchronizing, and updating server state in React applications a breeze.

**Usage:** Provides React hooks such as `useQuery` and `useMutation` for declaratively managing asynchronous server state, with built-in support for caching, background refetching, pagination, and invalidation. Written in TypeScript with full type-safety for robust, predictable data-fetching workflows.

---

## @tanstack/react-query-devtools

**Purpose:** A dedicated devtools package for TanStack Query that helps visualize all the inner workings of React Query, providing real-time insight into queries and mutations.

**Usage:** Provides the `ReactQueryDevtools` component, which renders a floating, interactive panel showing the status, data, and metadata of all active queries and mutations. Excluded from production builds by default; supports configuration options such as initial panel position, open state, and button placement.

---

## @tanstack/react-router

**Purpose:** A modern, type-safe, client-first routing library for React applications. Provides full awareness of all routes and their configuration — including path params, search params, and context — at every point in your code.

**Usage:** Offers fully type-safe routing with end-to-end TypeScript inference across route paths, path parameters, search parameters, and nested layouts, eliminating runtime routing bugs. Also supports file-based routing, JSON-safe search parameter parsing/serialization, data loaders, SSR, and streaming.

---

## @tanstack/react-router-devtools

**Purpose:** A separate devtools package for TanStack Router that helps visualize the inner workings of TanStack Router, saving developers hours of debugging.

**Usage:** Provides browser-based debugging capabilities including real-time inspection of router state, route matches, navigation history, and data loading status. The primary export `TanStackRouterDevtools` renders an interactive panel automatically excluded from production builds.

---

## @tanstack/react-table

**Purpose:** TanStack Table is a headless UI library for building powerful tables and data grids for React (and other frameworks), providing all core logic without shipping any components, markup, or styles.

**Usage:** Supports sorting, filtering, pagination, grouping, aggregation, column pinning, and row selection — all fully typed with TypeScript and controllable via an opt-in state management model. Exposes hooks and types that wrap the core table logic, giving developers complete freedom over markup, styling, and UI implementation.

---

## axios

**Purpose:** A promise-based HTTP client for Node.js and the browser. Isomorphic — runs in both environments using the same codebase, leveraging the native `http` module on the server and `XMLHttpRequest` in the browser.

**Usage:** Supports request/response interception, automatic JSON transformation, timeout configuration, and cancellation via AbortController. Ships with comprehensive built-in TypeScript type definitions, enabling type-safe requests and responses through generic parameters such as `axios.get<MyType>(url)`.

---

## class-variance-authority

**Purpose:** A TypeScript-first utility library for building type-safe, variant-driven UI components with composable class name management — without the need for CSS-in-JS solutions.

**Usage:** Provides a declarative `cva` API that lets developers define component variants, compound variants, and default variants with full TypeScript type inference. Especially well-suited for use with utility-first CSS frameworks like Tailwind CSS.

---

## clsx

**Purpose:** A tiny (239B) utility for constructing `className` strings conditionally, serving as a faster and smaller drop-in replacement for the `classnames` module.

**Usage:** Accepts strings, arrays, and objects as arguments to conditionally join CSS class names into a single string. Fully TypeScript-compatible; supports ESM, CommonJS, and UMD module formats.

---

## form-data

**Purpose:** A library to create readable `multipart/form-data` streams, used to submit forms and file uploads to other web applications.

**Usage:** Provides an `append` API to attach fields, files, and readable streams to a form payload, automatically handling boundary generation and content headers for multipart encoding. The resulting form object can be piped or passed directly to HTTP clients like `axios` or Node's built-in `http` module.

---

## lucide-react

**Purpose:** React components for Lucide icons that integrate seamlessly into React applications. Each icon is a fully-typed React component rendering as an optimized inline SVG.

**Usage:** Allows importing any Lucide icon as a React component with full TypeScript support, customizable via props such as `size`, `color`, and `strokeWidth`. Designed for excellent tree-shaking support, ensuring only used icons are included in the final bundle.

---

## next-themes

**Purpose:** An abstraction for themes in React apps, enabling perfect dark mode support. Handles theme state management, persistence via localStorage, system preference detection, and prevents Flash of Unstyled Content (FOUC) during SSR.

**Usage:** Provides a `ThemeProvider` component that automatically injects a script to apply the correct theme before the page loads, eliminating flashing. The `useTheme` hook gives components access to the current theme and a setter function, supporting light, dark, system, and custom themes.

---

## Radix UI React Primitives

**Packages:** `@radix-ui/react-avatar`, `@radix-ui/react-checkbox`, `@radix-ui/react-dialog`, `@radix-ui/react-dropdown-menu`, `@radix-ui/react-label`, `@radix-ui/react-radio-group`, `@radix-ui/react-scroll-area`, `@radix-ui/react-select`, `@radix-ui/react-separator`, `@radix-ui/react-slot`, `@radix-ui/react-tabs`, `@radix-ui/react-tooltip`

**Purpose:** An open-source, low-level UI component library for building high-quality, accessible design systems and web apps, focused on accessibility, customization, and developer experience. Provides unstyled, accessible React primitives.

**Usage:** Each package delivers a single, fully accessible and WAI-ARIA-compliant primitive that ships completely unstyled, giving teams full control over visual design without sacrificing behavior or keyboard/screen-reader support. Primitives are composable and tree-shakeable — consumers import only the packages they need and wire them together using the `@radix-ui/react-slot` Slot primitive.

---

## react

**Purpose:** A JavaScript library for creating user interfaces, designed to let you build UI out of individual reusable pieces called components. The `react` package contains only the core functionality necessary to define React components.

**Usage:** Enables developers to compose complex UIs from small, isolated components using patterns like hooks (e.g., `useState`, `useEffect`) and JSX syntax, with full TypeScript support. Renderer-agnostic — pairs with `react-dom` for web apps or `react-native` for mobile environments.

---

## react-dom

**Purpose:** The DOM-specific renderer for React web applications, serving as the entry point to the DOM and server renderers for React.

**Usage:** Provides core APIs such as `createRoot` and `hydrateRoot` (via `react-dom/client`) for mounting and rendering React component trees into browser DOM nodes, as well as `createPortal` for rendering content into arbitrary DOM locations. Also exposes server-side rendering utilities (via `react-dom/server`) and DOM-level helpers like `flushSync`.

---

## react-error-boundary

**Purpose:** A simple, reusable React error boundary component supporting all React renderers (React DOM and React Native). Enables graceful error handling in React component trees by catching errors during rendering and displaying a fallback UI.

**Usage:** Provides the `ErrorBoundary` component to catch render-time errors and display customizable fallback UI via render prop or component. Also exposes the `useErrorBoundary` hook, allowing errors from async code, event handlers, and effects to be manually forwarded to the nearest error boundary.

---

## react-hook-form

**Purpose:** A performant, flexible, and extensible forms library for React Hooks that simplifies form state management, validation, and submission with minimal re-renders.

**Usage:** Provides core hooks like `useForm`, `useController`, and `useFieldArray` to manage form registration, validation rules, and submission handling. Offers comprehensive TypeScript support with full type safety, enabling strongly-typed form patterns and compile-time validation.

---

## react-icons

**Purpose:** Include popular icons in React projects easily with react-icons, which utilizes ES6 imports allowing you to include only the icons your project is using.

**Usage:** Provides a vast collection of SVG icons from popular icon packs (Font Awesome, Material Design, Bootstrap Icons, and more), each wrapped as a fully typed React component with TypeScript support. Icons can be individually imported from their respective sub-packages (e.g., `react-icons/fa`), ensuring efficient tree-shaking and minimal bundle size.

---

## sonner

**Purpose:** An opinionated, lightweight toast notification component for React, designed to be simple, accessible, and visually clean out of the box.

**Usage:** Provides a straightforward API via the `toast()` function, supporting multiple toast types such as success, error, warning, info, loading, and promise-based notifications. Includes full TypeScript support, customizable styling, stacking/queuing behavior, and a drop-in `<Toaster />` component for easy integration.

---

## tailwind-merge

**Purpose:** A utility function to efficiently merge Tailwind CSS classes in JavaScript/TypeScript without style conflicts. Intelligently resolves class collisions so that the last conflicting class always wins.

**Usage:** The core `twMerge` function accepts multiple class name strings or arrays and returns a single, conflict-free merged class string based on Tailwind's default configuration. For custom Tailwind configurations, `extendTailwindMerge` allows extending or overriding the default merging logic.

---

## tailwindcss

**Purpose:** A utility-first CSS framework for rapidly building custom user interfaces directly in your markup, without ever leaving your HTML.

**Usage:** Provides a comprehensive set of low-level utility classes (e.g., `flex`, `pt-4`, `text-center`) composable to build any design without writing custom CSS. Integrates seamlessly into TypeScript-based projects via npm and supports configuration through a `tailwind.config` file for theme customization, plugins, and content purging.

---

## zod

**Purpose:** A TypeScript-first schema declaration and validation library that allows defining schemas for validating data — from simple strings to complex nested objects — with static type inference.

**Usage:** Enables developers to declare schemas once and automatically infer corresponding static TypeScript types, eliminating redundancy between runtime validation and compile-time type safety. Supports primitives, objects, arrays, unions, and more — suitable for validating API responses, form inputs, and environment configurations.