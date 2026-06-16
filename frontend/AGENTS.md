<!-- UNOPLAT_CODE_CONFLUENCE_CONTEXT:BEGIN -->
<CRITICAL_INSTRUCTION>

> Generated from branch `master` at commit `f6c2e534c3a04b123670119df7889ee73718235d` (2026-03-17). Content may become stale as new commits land.

</CRITICAL_INSTRUCTION>

## Engineering Workflow

| Stage | Command | Config File |
|---|---|---|
| install | `npm ci` | `package.json` |
| build | `npm run build` | `tsconfig.build.json` |
| dev | `npm run dev` | `vite.config.ts` |
| test | `npm run test` | `playwright.config.ts` |
| lint | `npm run lint` | `biome.json` |
| type_check | `npx tsc --noEmit` | `tsconfig.json` |

## Dependency Guide

For a full catalog of all runtime and build-time dependencies — including purpose and usage details for each — see [`dependencies_overview.md`](./dependencies_overview.md).

## Business Logic Domain

Detailed domain coverage — including auth flows, role-based access control, user/item CRUD, and key source file responsibilities — is documented in [`business_logic_references.md`](./business_logic_references.md).

## App Interfaces

A full inventory of inbound, outbound, and internal interface constructs for this frontend is documented in [`app_interfaces.md`](./app_interfaces.md).

<!-- UNOPLAT_CODE_CONFLUENCE_CONTEXT:END -->
