# Starter Structure

## Use This Reference For

- Locating the official starter entrypoints
- Understanding where storefront code belongs
- Finding environment and routing boundaries before editing

## Baseline Assumption

- From Vendure v3.5.2 onward, `@vendure/create` can include the official Next.js storefront starter by default.
- Expect a new project to separate backend and storefront concerns, often as sibling apps in the same repo.

## Files to Locate First

- The storefront app root, often `apps/storefront` or the repo-specific equivalent
- Environment variable files used by the storefront
- Route and layout entrypoints that define the customer-facing shell
- Shared API client or GraphQL utility modules

## Structure Rules

- Keep Shop API access centralized enough that session handling and endpoint configuration stay consistent.
- Follow the route and component conventions already established by the starter rather than inventing a second architecture.
- Keep admin concerns out of the storefront app.

## Startup Checklist

1. Confirm the real storefront app root.
2. Confirm how the repo configures the Shop API endpoint.
3. Confirm where shared GraphQL fragments or typed helpers live.
4. Confirm whether the page should be server-rendered, interactive, or split across both concerns.
