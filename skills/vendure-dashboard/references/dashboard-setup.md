# Dashboard Setup

## Use This Reference For

- Wiring a plugin into the modern Dashboard
- Understanding the expected project setup for Dashboard development
- Locating the entry files that make Dashboard extensions discoverable

## Baseline Assumption

- New projects created with `@vendure/create` from Vendure v3.5.0 onward treat `@vendure/dashboard` as the standard admin UI path.
- This skill assumes that baseline and does not cover the legacy Angular Admin UI.

## Setup Rules

- Ensure the project includes `@vendure/dashboard`.
- Ensure the project has a `vite.config.mts` or repo-specific Vite config that uses `vendureDashboardPlugin`, points to `vendureConfigPath`, sets the Admin API host, and defines `gqlOutputPath`.
- Ensure `DashboardPlugin.init(...)` is configured in `vendure-config.ts` when the app serves the Dashboard.
- Ensure the plugin metadata includes `dashboard: './dashboard/index.tsx'` so Vendure can discover the extension entrypoint.

## Files to Inspect First

- `src/vendure-config.ts`
- `vite.config.mts`
- `tsconfig.dashboard.json` or the repo-specific Dashboard TypeScript config
- `src/plugins/feature/dashboard/index.tsx`
- `src/gql/graphql-env.d.ts` or the repo-specific Dashboard GraphQL output path

## Setup Checklist

1. Confirm the Dashboard is enabled in the server config.
2. Confirm the plugin exposes a dashboard entry file.
3. Confirm GraphQL type output is configured and importable.
4. Confirm the Dashboard build path and runtime route match the project configuration.
