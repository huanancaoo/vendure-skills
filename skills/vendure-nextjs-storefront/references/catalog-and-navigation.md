# Catalog and Navigation

## Use This Reference For

- Product listing pages
- Product detail pages
- Collection navigation
- Search and facet filtering

## Source of Truth

- Use collections to drive storefront navigation and category structure.
- Use search and facets to drive filterable discovery experiences.
- Use product and variant data from the Shop API for PDP and merchandising views.

## Product Listing Rules

- Build collection pages around collection identity plus search or listing data.
- Keep filter state aligned with Vendure facet semantics rather than inventing unrelated category models.
- Distinguish between collection-driven browsing and free-text search, even when both share UI building blocks.

## Product Detail Rules

- Query products by stable storefront identifiers such as slug when the route is slug-based.
- Include the fields required for variant selection, images, pricing, and stock display in one intentional page contract.
- Keep add-to-cart flows anchored to variant IDs, not to product-level assumptions.

## Navigation Rules

- Derive menus from collection hierarchy when the store uses collections as navigation.
- Use `collections(options: { topLevelOnly: true })` for top-level navigation and include `parentId` when the UI needs to build a tree.
- Respect private versus public collection visibility.
- Avoid hardcoding parallel trees that drift away from the real catalog structure.
