# Dashboard GraphQL Workflow

## Use This Reference For

- Using Dashboard GraphQL type safety
- Writing queries and mutations for Dashboard extensions
- Keeping Admin API documents and UI code in sync

## Core Rule

Treat the Dashboard as a typed Admin API client. Use the Dashboard Vite plugin and `gql.tada` output; do not set up the legacy Angular Admin UI codegen path for React Dashboard work.

## Workflow

1. Confirm the backend plugin exposes the required Admin API fields.
2. Ensure `vendureDashboardPlugin` can load the Vendure config through `vendureConfigPath` and introspect the Admin API through the configured API host.
3. Ensure `gqlOutputPath` and the `@/gql` alias point to the generated Dashboard GraphQL environment files.
4. Define Dashboard operations with `import { graphql } from '@/gql'`.
5. Use Dashboard data helpers such as `api.query`, `api.mutate`, `useQuery`, and `useMutation` with those typed documents.

## Document Design

- Keep operations narrow and page-specific.
- Extend existing detail or list documents only when the page truly needs extra fields.
- Keep naming aligned with the plugin feature so searchability stays high.
- Re-run `npx vendure schema --api admin` only for IDE GraphQL autocomplete or plugin-level schema workflows, not as a replacement for Dashboard `gql.tada` typing.

## Failure Patterns

- Missing fields usually means the backend plugin is not exposing them, not that the Dashboard typing layer is wrong.
- Type generation issues often start from Vite config, Vendure config discovery, `gqlOutputPath`, path aliases, or an unreachable local server.
