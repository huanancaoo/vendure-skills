# Shop API Data Flows

## Use This Reference For

- Storefront queries and mutations
- Session-aware customer and cart behavior
- Price, error, and custom field semantics

## Core Rule

Treat the storefront as a typed Shop API client with session-backed state. Design flows around the server contract, not around local UI assumptions.

## Session Rules

- The current cart is the active order bound to the current session.
- Guest and authenticated customers both operate on the Shop API, but only registered customers have account capabilities.
- Preserve session continuity intentionally when designing data fetching and mutations.
- Check the backend `authOptions.tokenMethod` before choosing session transport.
- For cookie sessions, send credentials with every browser request.
- For bearer sessions, read the `vendure-auth-token` response header and attach it to later requests as `Authorization: Bearer <token>`.

## Response Design

- Handle GraphQL union results explicitly for mutations that can return domain errors.
- Keep fragments stable for repeated cart and customer shapes.
- Request only the fields a page or mutation handler actually needs.

## Storefront Codegen

- Use the Storefront GraphQL Codegen path for customer-facing code, not the plugin or Dashboard codegen path.
- Point the schema at `http://localhost:3000/shop-api` unless the project configures a different Shop API URL.
- Configure GraphQL Code Generator with `Money: 'number'` for the `Money` scalar and `enumValues: 'keep'` under `namingConvention`.
- Use the generated `graphql()` function from the storefront `src/gql` output when defining queries and mutations.

## Money and Custom Data

- Vendure returns money values in the smallest currency unit, so always format before rendering.
- Choose deliberately between base fields such as `price`, `linePrice`, and `total`, and tax-inclusive fields such as `priceWithTax`, `linePriceWithTax`, and `totalWithTax`.
- Prefer a single storefront pricing display convention per market so PDP, PLP, cart, checkout, and structured data do not disagree.
- Only rely on plugin custom fields or custom types after the backend has exposed them through Shop API intentionally.

## Review Checklist

1. Does the flow depend on active order, active customer, or neither.
2. Are error results handled explicitly rather than assumed away.
3. Are prices formatted rather than rendered raw.
4. Is the data contract really available on Shop API.
