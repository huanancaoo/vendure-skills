# Dashboard Navigation and Routes

## Use This Reference For

- Custom pages
- Sidebar entries
- Custom navigation sections
- Route-level data loading

## Core Rule

Register Dashboard pages through `defineDashboardExtension({ routes: [...] })` and attach navigation only when the page should appear in the left menu.

## Route Design

- Give each route a stable `path` owned by the plugin feature.
- Use `navMenuItem` when the page belongs in an existing or custom section.
- Use `loader` for route-level data preparation when the page depends on initial Admin API state.
- Keep authentication assumptions explicit and aligned with Dashboard defaults.

## Navigation Design

- Reuse a built-in section when the feature naturally belongs there.
- Add a custom section only when the feature introduces a genuinely separate admin workflow.
- Keep route titles and nav labels aligned with the domain concept rather than with implementation names.
- Use array-form `navSections` to add sections declaratively.
- Use function-form `navSections` only when you need to move, remove, or reorder existing items; return a new config object rather than mutating the input.
- Remember that the function form is available from Vendure v3.6.0 onward.

## Review Checklist

1. Does the route belong to the plugin that owns the feature.
2. Is the page placed in the most natural nav section.
3. Is any route loader fetching only the data needed for first render.
4. Could the page be a page block or detail-form extension instead of a full custom route.
