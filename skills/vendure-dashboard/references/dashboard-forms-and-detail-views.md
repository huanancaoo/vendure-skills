# Dashboard Forms and Detail Views

## Use This Reference For

- Replacing or extending inputs on existing detail pages
- Registering custom field components
- Building precise form behavior for admin workflows

## Two Main Paths

- Use `customFormComponents` when you want a reusable component that can back custom fields or configurable operations.
- Use `detailForms` when you need to target a specific page, block, and field on an existing detail view.

## Targeting Rules

- Identify the real `pageId` and `blockId` before editing extension code.
- Replace only the fields that need custom behavior.
- Keep form components aligned with the Dashboard form contract so change handling, blur handling, and disabled state remain correct.

## Component Rules

- Prefer Dashboard-provided UI primitives for consistent styling.
- Show validation feedback through the form APIs instead of inventing separate local error state.
- Keep components focused on rendering and field interaction, not on backend orchestration.

## When to Escalate Back to Backend

- When a new form field needs new Admin API schema
- When a detail page needs data that the backend does not expose yet
- When the UI would otherwise duplicate business rules that should live in services or resolvers
