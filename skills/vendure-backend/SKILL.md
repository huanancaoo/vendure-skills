---
name: vendure-backend
description: Vendure backend development for the modern new-project baseline created with @vendure/create. Use when Codex needs to work on VendureConfig, vendure-config.ts, plugins, entities, custom fields, services, resolvers, Admin API or Shop API extensions, workers, job queues, events, permissions, or search. Load for backend-only Vendure work and do not use it for Dashboard UI or storefront implementation.
---

# Vendure Backend

## Overview

Build Vendure backend capabilities for the current new-project baseline. Keep this skill focused on server configuration, plugins, entities, GraphQL extensions, workers, and backend-only integrations.

If the task is a React Dashboard extension, use `vendure-dashboard`. If the task is a Next.js storefront feature, use `vendure-nextjs-storefront`.

## Load These References First

- Read `references/project-bootstrap.md` when locating entrypoints, project layout, or bootstrap commands.
- Read `references/plugin-architecture.md` before creating or restructuring a plugin.
- Read `references/entities-and-custom-fields.md` before modeling data or extending existing Vendure entities.
- Read `references/graphql-api-extensions.md` before adding schema, resolvers, queries, or mutations.
- Read `references/worker-job-queue.md` before designing long-running or asynchronous work.
- Read `references/operations-debugging.md` when troubleshooting runtime, schema, migration, or worker issues.

Load at least one relevant reference before changing code. Load two or more when the task spans plugin shape plus API shape, or data modeling plus background work.

## Backend Workflow

1. Classify the request as configuration, plugin composition, data modeling, API extension, background processing, or operational debugging.
2. Load the matching reference files before choosing an implementation path.
3. Keep the capability inside a plugin unless the change is truly global bootstrap configuration in `vendure-config.ts`.
4. Decide early whether the change belongs in Admin API, Shop API, or both. Do not expose administrator semantics through the Shop API.
5. Decide whether the data should be a custom field on an existing entity or a first-class entity with its own lifecycle.
6. Decide whether any work can block a request. If it can, move it behind a worker or queue.
7. Check whether the change also requires permissions, events, search indexing, or migrations.

## Plugin Boundaries

- Put backend business capability behind a plugin decorated with `VendurePlugin`.
- Use `PluginCommonModule` unless a narrower module arrangement is clearly better.
- Keep resolvers thin and push orchestration into services.
- Use the plugin `configuration` hook only for bootstrap-time configuration changes.
- Prefer custom fields when extending an existing Vendure entity with lightweight extra data.
- Prefer a dedicated entity when the feature has its own lifecycle, relations, or query surface.
- Treat dashboard rendering and storefront rendering as separate concerns owned by other skills.

## Common Mistakes

- Do not mix Dashboard extension code or Next.js storefront code into backend guidance.
- Do not use the Shop API for administrator workflows.
- Do not block API requests with heavy import, export, notification, indexing, or batch processing.
- Do not add custom fields when the feature really needs its own entity and service boundary.
- Do not start from legacy project layouts or older Admin UI assumptions when the task targets a new Vendure project.
