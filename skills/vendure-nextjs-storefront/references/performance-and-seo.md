# Performance and SEO

## Use This Reference For

- Metadata and structured data
- Image delivery
- Caching and overfetch reduction
- Search-friendly storefront routing

## Core Rule

Keep the storefront fast by fetching only the data needed for the current page and by letting Next.js and Vendure each do the job they are good at.

## Performance Rules

- Keep shared Shop API queries focused so pages do not overfetch catalog data.
- Reuse storefront data contracts for repeated surfaces such as nav, cart summary, and product cards.
- Use Vendure asset transforms and Next.js image strategy intentionally instead of rendering raw originals everywhere.

## SEO Rules

- Generate stable metadata from collection and product data.
- Keep canonical product and collection URLs aligned with the routing structure.
- Add structured data where the storefront needs product-rich search visibility.
- Use the same tax-inclusive or tax-exclusive price convention in structured data that the customer sees on the page.
- Treat faceted and search pages carefully so crawlable URLs remain intentional.

## Review Checklist

1. Is the page fetching only what it renders.
2. Are image URLs and transforms appropriate for the displayed size.
3. Are metadata and structured data based on real catalog data.
4. Does the route structure stay stable for sharing and indexing.
