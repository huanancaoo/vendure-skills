# Entities and Custom Fields

## Use This Reference For

- Choosing between custom fields and a new entity
- Modeling relations
- Planning migrations and query shape

## Decision Rule

- Use a custom field when the data extends an existing Vendure entity and has no independent lifecycle.
- Use a new entity when the feature needs its own records, relations, permissions, queries, or mutation flow.

## Prefer Custom Fields When

- The data is a small extension of `Product`, `Customer`, `Order`, or another built-in entity.
- The data can be loaded naturally with the parent entity.
- The feature does not need its own repository-style service boundary.

## Prefer a New Entity When

- The feature has its own lifecycle or status transitions.
- The feature needs one-to-many or many-to-many relations beyond a simple annotation.
- The feature needs dedicated Admin API or Shop API queries and mutations.
- The feature will likely grow into a plugin-owned capability.

## Modeling Rules

- Keep ownership obvious. A feature entity should have a clear aggregate root or primary workflow owner.
- Name relations from the business concept, not from the UI that happens to display them.
- Decide whether storefront consumers need the data before exposing it through Shop API.
- If the entity should be extensible later, design it so custom fields can be added intentionally rather than by accident.

## Migration Implications

- Any new entity or schema-affecting relation change usually implies a migration.
- Custom field changes also affect schema and often require migration work.
- Do not treat data modeling as a pure TypeScript change. Always follow the database path through to runtime.
