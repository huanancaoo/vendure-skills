# Dashboard Layout, Widgets, and Shell Extensions

## Use This Reference For

- Insights widgets
- Page blocks
- Action bar items
- Toolbar items
- Alerts
- Login page customizations
- Custom history entries
- Data table customization

## Choose the Right Extension Surface

- Use a widget when the feature belongs on the Insights page or a metrics-oriented admin surface.
- Use a page block when the feature augments an existing page layout.
- Use an action bar item when the feature is a contextual page action.
- Use a toolbar item when the feature belongs in the top-level Dashboard shell header. Keep it compact and position it relative to built-ins such as `alerts` when needed.
- Use an alert when the Dashboard should surface a global admin-visible condition.
- Use a login customization only when the sign-in experience itself needs plugin-owned UI.
- Use a history entry component when the Order or Customer history timeline needs plugin-specific rendering.
- Use a data table extension when list behavior, columns, or bulk actions need to change.

## Data Table Rules

- Extend existing list documents only with fields the UI actually uses.
- Target the real `pageId` and `blockId` so the customization lands on the intended table.
- Use custom display components when the built-in rendering is not enough, but keep them domain-specific.

## Action and Widget Rules

- Tie page actions to permissions when the underlying backend capability is restricted.
- Keep widgets and blocks focused on one admin question or one action path.
- Prefer explicit identifiers when positioning action bar items relative to existing controls.
- Do not put workflow logic in alerts, toolbar items, or history renderers; use them to surface state and trigger existing backend actions.

## Review Checklist

1. Did you choose the smallest extension surface that fits the need.
2. Does the extension rely on fields the Admin API actually exposes.
3. Are permissions or page context handled explicitly.
4. Is the customization anchored to the correct page, block, item, or shell location.
