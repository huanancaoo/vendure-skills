# Operations and Debugging

## Use This Reference For

- Startup failures
- GraphQL schema not appearing
- Worker tasks not executing
- Migration or runtime wiring issues

## First Checks

1. Confirm the feature plugin is actually registered in `vendure-config.ts`.
2. Confirm the worker bootstrap loads the plugin if the feature depends on background execution.
3. Confirm schema extension files are connected to the plugin metadata that Vendure reads.
4. Confirm the project is running the expected server or worker command for the repo layout.

## API Debugging

- If a query or mutation is missing, inspect plugin registration before debugging the resolver body.
- If an Admin API field works but the storefront cannot see it, verify that the field belongs on Shop API and was exposed there intentionally.
- If a resolver compiles but fails at runtime, inspect `RequestContext`, permissions, and service injection first.

## Data Debugging

- If data is present in the database but not in API responses, inspect custom field exposure and relation loading choices.
- If a schema change compiles but runtime breaks, verify the database migration state and execution result rather than assuming TypeScript is enough.

## Worker Debugging

- If jobs queue but never finish, inspect worker startup before queue handler logic.
- If background tasks cannot access expected providers, verify plugin registration on the worker side.

## Recovery Mindset

- Trace the full path: registration, bootstrap, schema, service, persistence, worker.
- Fix the first broken link in that path instead of layering local workarounds on top.
