---
name: vendure-nextjs-storefront
description: Vendure storefront development for the official Next.js starter and Shop API integration. Use when Codex needs to build or modify product listing pages, product detail pages, collection navigation, customer authentication, active order cart flows, checkout, search with facets, SEO, or storefront data fetching against Vendure Shop API. Do not use this skill for Remix, Qwik, Angular, or other storefront frameworks.
---

# Vendure Next.js Storefront

## Overview

Build customer-facing storefront features for the official Vendure Next.js starter. Keep this skill focused on Shop API data flows, Next.js storefront structure, catalog browsing, authentication, cart and checkout, and storefront-facing SEO and performance.

If a feature needs new Shop API fields, new custom fields, or new backend mutations first, switch to `vendure-backend` before changing the storefront.

## Load These References First

- Read `references/starter-structure.md` before locating app entrypoints, environment variables, or route structure.
- Read `references/shop-api-data-flows.md` before writing queries, mutations, or session-dependent data flows.
- Read `references/catalog-and-navigation.md` before building collection pages, product lists, product detail pages, search, or facet filtering.
- Read `references/auth-cart-checkout.md` before touching customer login, registration, active order, cart, or checkout flows.
- Read `references/performance-and-seo.md` before changing page metadata, image behavior, caching, or structured data.

Load the Shop API reference for every data-bearing change. Load the catalog or auth reference depending on whether the user-facing feature is browse-oriented or transaction-oriented.

## Storefront Workflow

1. Confirm that the task belongs to the official Next.js storefront starter or its repo-specific derivative.
2. Decide whether the change is structural, catalog-driven, session-driven, or performance-driven.
3. Load the matching reference files before choosing components or queries.
4. Build around Shop API contracts first, then fit the UI into the existing Next.js route and component structure.
5. Keep active order, guest checkout, and authenticated customer flows explicit so session state does not become implicit UI magic.
6. If the storefront needs backend fields that do not exist yet, stop and add them through `vendure-backend` first.

## Shop API Integration Rules

- Treat the storefront as a Shop API client only. Do not design against Admin API semantics.
- Model the cart as the active order, not as a separate client-only entity.
- Format prices deliberately because the Shop API returns money in the smallest currency unit.
- Build collection navigation and filter UI from Vendure collections, search results, and facets rather than from hardcoded category trees.
- Expose plugin custom data in the storefront only when the backend intentionally makes it available through the Shop API.

## Common Mistakes

- Do not widen this skill into Remix, Qwik, Angular, or framework-agnostic storefront guidance.
- Do not hardcode catalog navigation when the source of truth is collections and search facets.
- Do not treat cart state as detached from the active order session model.
- Do not assume customer account flows are the same as administrator authentication.
- Do not patch around missing Shop API data in the UI when the real fix belongs in the backend plugin.
