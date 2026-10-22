# Architecture and implementation checklist

## Current layout

- `client/index.html`, `client/styles.css`, `client/src/app.js`: responsive browser application and same-origin API client.
- `server/src/server.js`: static server, versioned REST API, session handling, validation and domain calculations.
- `data/`: local per-account records at runtime; ignored by Git.
- `docs/api.md`, `docs/security.md`, `docs/tinyfish-integration.md`: current contracts and explicit limitations.

## Implemented

- Registration/login, scrypt password hashes, HMAC-signed HttpOnly cookie and logout.
- Account-scoped invoices and payments; paise-based balances; calculated due statuses.
- Dashboard, aging buckets, customer totals, settings, CSV, editable reminder history, checklist and research unavailable history.
- Request size limit, same-origin operation, CSP, error responses, input bounds, no secrets in browser code.

## Incomplete against master brief

- React/Vite/TypeScript, Tailwind, React Router, TanStack Query, RHF/Zod, chart library, component/icon system.
- Express, Prisma/PostgreSQL schema/migrations, transactional repository, seed and health endpoints.
- LLM integration; reminder UI has a deterministic fallback only.
- TinyFish live integration and independently verified official API contract.
- Authentication/research/LLM rate limits, CSRF protections, automated tests, deployment pipeline, accessibility audit.
- Invoice edit interface, payment corrections, reminder filter/search, research source UI (there are no live results), profile/account deletion and retention tools.

## Next phases

1. Choose and document supported TinyFish contract from its current official docs; implement adapter and live verification.
2. Add Postgres/Prisma schema and migrate local domain operations into a repository layer.
3. Move to React/Vite/TypeScript and add accessible form validation and charting.
4. Add tests for calculations, auth, ownership, external failures and browser flows; configure CI.
5. Harden production: rate limits, CSRF decision, retention/deletion, logs, monitoring, HTTPS and backups.
