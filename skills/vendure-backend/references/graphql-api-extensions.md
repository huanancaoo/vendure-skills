# GraphQL API Extensions

## Use This Reference For

- Adding Admin API or Shop API schema
- Writing resolvers
- Choosing permission and request-context boundaries

## API Surface Rule

- Use Admin API for administrator workflows, configuration tasks, and back-office operations.
- Use Shop API for customer-facing storefront capabilities.
- Expose a capability through both APIs only when the same domain concept genuinely has both back-office and customer-facing behavior.

## Implementation Shape

```ts
export const adminApiExtensions = gql`
  extend type Mutation {
    runFeature(input: RunFeatureInput!): FeatureResult!
  }
`
```

- Keep schema extension files focused on GraphQL types and signatures.
- Keep resolver classes thin and route behavior into services.
- Use `RequestContext` deliberately so channel, active user, and permissions remain explicit.

## Codegen and Types

- Use `npx vendure add` and select GraphQL code generation when setting up plugin codegen in a project that does not have it yet.
- Run `npx vendure schema` or `npx vendure schema --api admin` when the project needs a generated `schema.graphql` for plugin codegen or IDE autocomplete.
- Use generated operation argument types in resolvers and service methods instead of hand-writing argument shapes.
- Re-run the project codegen command whenever plugin GraphQL operations or schema extensions change.

## Resolver Rules

- Validate what the API layer must validate, then delegate.
- Return stable shapes that reflect the domain rather than leaking internal persistence details.
- Apply permissions explicitly for Admin API mutations and sensitive queries.
- Use `@Transaction()` on mutating resolver methods that must be atomic.
- Use `@Allow()` with feature-specific permissions for protected Admin API resolvers.
- Pass `RequestContext` through to every service method that reads or writes data.
- Keep Shop API fields intentionally minimal and customer-safe.

## Custom Field Interaction

- When Shop API needs custom field data, make that exposure an explicit decision.
- Do not mirror every Admin API field into the Shop API by default.
- Revisit search and indexing if a new field affects listing or filtering behavior.

## Review Checklist

1. Is the capability on the correct API surface.
2. Does the resolver delegate to a service instead of owning business logic.
3. Are permissions explicit where needed.
4. Does the response shape match the domain rather than the table layout.
5. Does the change require worker support, indexing, or migration follow-up.
