# Project Bootstrap

## Scope

Use this reference when you need to locate the modern Vendure entrypoints, understand the generated layout, or decide where backend changes belong in a new project.

## New-Project Baseline

- Start from `npx @vendure/create`.
- Expect a current project to use the modern Dashboard and to support the official Next.js storefront starter as a separate concern.
- Keep backend work centered on the server application rather than on Dashboard or storefront packages.

## Files to Find First

- `src/vendure-config.ts` or `vendure-config.ts`: global bootstrap configuration.
- `src/index.ts`, `src/server.ts`, or the project bootstrap entry: server startup wiring.
- `src/index-worker.ts` or equivalent worker bootstrap file: worker startup wiring.
- `src/plugins/`: plugin home when the project keeps custom backend capabilities together.

## Where to Place Changes

- Put global configuration in `vendure-config.ts` only when it affects application bootstrap.
- Put feature logic in a plugin when the task introduces a reusable capability, schema, service, or entity.
- Put worker startup changes in the worker bootstrap file, not in request handlers.

## Commands to Prefer

- Use `npx @vendure/create` to generate a new project baseline.
- Use `npx vendure add` when the project already exists and you need Vendure-provided scaffolding.
- Use the project's normal dev command to run the server and worker in the shape the repo already expects.

## Bootstrap Checklist

1. Confirm the real location of `vendure-config.ts`.
2. Confirm whether the task belongs in an existing plugin or needs a new plugin.
3. Confirm whether a worker bootstrap file already exists.
4. Confirm whether the change affects Admin API, Shop API, or both.
5. Confirm whether the feature needs migration, permissions, or search reindexing.
