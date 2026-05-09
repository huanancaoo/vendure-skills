# Vendure Skills

Agent skills for Vendure backend, React Dashboard, and official Next.js storefront development.

## Skills

- `vendure-backend`: Vendure backend, plugins, entities, GraphQL API extensions, workers, job queues, and configuration.
- `vendure-dashboard`: Modern React `@vendure/dashboard` extensions. This skill does not cover the legacy Angular Admin UI.
- `vendure-nextjs-storefront`: Official Vendure Next.js storefront starter and Shop API integration. This skill does not cover Remix, Qwik, Angular, or other storefront routes.

## Install

List available skills:

```bash
npx skills add huanancaoo/vendure-skills --list
```

Install all skills globally for supported agents:

```bash
npx skills add huanancaoo/vendure-skills --all -g
```

Install a single skill:

```bash
npx skills add huanancaoo/vendure-skills --skill vendure-backend -g
npx skills add huanancaoo/vendure-skills --skill vendure-dashboard -g
npx skills add huanancaoo/vendure-skills --skill vendure-nextjs-storefront -g
```

## Scope

These skills target modern Vendure projects and keep responsibilities separate: backend capability work, Dashboard extension work, and storefront Shop API work.
