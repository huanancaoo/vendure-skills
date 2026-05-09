# Auth, Cart, and Checkout

## Use This Reference For

- Customer login and registration
- Active order queries and mutations
- Cart display and editing
- Checkout orchestration

## Authentication Rules

- Use storefront customer flows, not administrator login semantics.
- Distinguish guest checkout from registered account behavior.
- Keep account entrypoints aligned with the authentication strategy the backend actually uses.

## Cart Rules

- Vendure has no separate Cart entity. A cart is an `Order` in the `AddingItems` state.
- The active order is resolved from the current session, so cart mutations do not need an order ID.
- Query `activeOrder` when the UI needs current cart state.
- Use `addItemToOrder`, `adjustOrderLine`, `removeOrderLine`, and coupon mutations as the canonical cart mutation path.
- Handle inventory or validation errors explicitly because cart mutations can return union error results.

## Checkout Rules

- Treat checkout as the progression of the active order, not as a separate client wizard detached from server state.
- Keep address, shipping, payment, and order-state transitions aligned with the Shop API workflow exposed by the backend.
- Expect cart edits to stop once the order leaves `AddingItems` and moves toward payment arrangement.
- Avoid skipping validation that the backend will enforce anyway.

## Customer Account Rules

- Use `activeCustomer` to decide whether the shopper is signed in.
- Use login, logout, registration, and verification flows that match the configured authentication strategy.
- Remember that guest customers have no account permissions even though they can place orders.
