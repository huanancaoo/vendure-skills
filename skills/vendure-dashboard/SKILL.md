---
name: vendure-dashboard
description: React Dashboard extension development for Vendure projects using @vendure/dashboard and defineDashboardExtension. Use when Codex needs to add or modify dashboard routes, nav sections, page blocks, widgets, alerts, login customizations, history entries, detail forms, data tables, action bar items, toolbar items, custom form components, GraphQL data fetching, or plugin dashboard entry files. Use only for the modern Dashboard and not for the legacy Angular Admin UI.
---

# Vendure Dashboard

## Overview

Build admin-facing UI extensions for the modern React Dashboard. Keep this skill focused on `defineDashboardExtension`, plugin dashboard entry files, Dashboard-specific GraphQL typing, and admin UI composition.

If the task needs new entities, new Admin API fields, permissions, or worker behavior first, switch to `vendure-backend` before building the UI.

## Load These References First

- Read `references/dashboard-setup.md` before wiring a plugin into the Dashboard or adjusting project configuration.
- Read `references/dashboard-navigation-and-routes.md` before adding routes, nav items, or custom sections.
- Read `references/dashboard-forms-and-detail-views.md` before replacing inputs or extending detail pages.
- Read `references/dashboard-widgets-and-data-tables.md` before adding widgets, page blocks, action bar items, toolbar items, alerts, history entries, login customizations, or list customizations.
- Read `references/dashboard-graphql-workflow.md` before writing queries, mutations, fragments, or generated types for Dashboard code.

Load the GraphQL workflow reference whenever the UI needs data. Load the setup reference whenever the plugin entry file or project configuration is part of the change.

## Dashboard Extension Workflow

1. Find the plugin that owns the feature and confirm it exposes `dashboard: './dashboard/index.tsx'` or the repo-specific equivalent.
2. Decide which extension surface you are targeting: route, nav section, page block, widget, alert, login customization, history entry, detail form, data table, action bar item, toolbar item, or custom form component.
3. Load the reference file for that extension surface before editing code.
4. Keep the Dashboard entry file centered on `defineDashboardExtension(...)` and wire only the extension points the feature actually needs.
5. Use Admin API data intentionally and keep GraphQL documents, generated types, and UI components aligned.
6. If the UI requires backend schema or permission changes, stop and add those through `vendure-backend` first.

## GraphQL and UI Coupling Rules

- Treat the Dashboard as an Admin API client. Do not design it around Shop API assumptions.
- Keep GraphQL documents near the Dashboard code that consumes them so UI intent and data shape stay aligned.
- Use the generated `graphql()` helper imported from `@/gql` and the Dashboard `gql.tada` environment types rather than hand-waving field names through the UI.
- Prefer Dashboard-provided components and design tokens so the extension stays visually consistent with the host app.
- Target existing pages and blocks precisely by page ID and block ID instead of guessing layout hooks.

## Common Mistakes

- Do not output legacy Angular Admin UI patterns, modules, or extension APIs.
- Do not build dashboard screens before the plugin exposes the backend fields or permissions they depend on.
- Do not place business logic in Dashboard components when the behavior belongs in the backend plugin.
- Do not extend random pages by guesswork when dev mode or reference IDs can identify the real targets.
- Do not widen this skill into storefront work or backend-only design.
