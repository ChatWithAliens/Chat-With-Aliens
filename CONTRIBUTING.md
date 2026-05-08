# Contributing to Chat with Aliens

Thank you for your interest in contributing. This document covers how to get the project running locally and the conventions we follow.

## Getting Started

### Prerequisites

- Node.js 20+
- pnpm 9+
- PostgreSQL 15+

### Setup

```bash
# Install dependencies
pnpm install

# Copy environment variables
cp .env.example .env
# Fill in your DATABASE_URL and XAI_API_KEY (or OPENAI_API_KEY)

# Push the database schema
pnpm --filter @workspace/db run push

# Start the API server
pnpm --filter @workspace/api-server run dev

# Start the frontend (separate terminal)
pnpm --filter @workspace/chat-with-aliens run dev
```

## Project Structure

```
artifacts/
  api-server/        # Express 5 backend
  chat-with-aliens/  # React + Vite frontend
lib/
  db/                # Drizzle ORM schema and client
  api-spec/          # OpenAPI spec + code generation
  api-client-react/  # Generated React Query hooks
scripts/             # Utility scripts (PDF ingestion, OCR)
```

## Code Conventions

- **TypeScript everywhere** — no plain JS files in `src/`
- **Zod for validation** — all API inputs and outputs validated with Zod schemas derived from the OpenAPI spec
- **No `console.log` in server code** — use `req.log` in route handlers and the `logger` singleton elsewhere
- **OpenAPI first** — define new endpoints in `lib/api-spec/openapi.yaml`, then run `pnpm --filter @workspace/api-spec run codegen` to regenerate hooks and schemas
- **Mobile-first CSS** — Tailwind classes without a breakpoint prefix apply to mobile; use `sm:` and `md:` for larger screens

## Regenerating API Code

After changing `lib/api-spec/openapi.yaml`:

```bash
pnpm --filter @workspace/api-spec run codegen
```

This regenerates React Query hooks and Zod schemas. Commit the generated files alongside the spec change.

## Database Migrations

After changing `lib/db/src/schema/`:

```bash
pnpm --filter @workspace/db run push
```

This applies schema changes to your local database.

## Pull Requests

- Keep PRs focused on a single concern
- Include a clear description of what changed and why
- Ensure `pnpm run typecheck` passes before opening a PR
- Existing UI and API behavior should not regress unless the PR explicitly changes it

## Reporting Issues

Open a GitHub issue with:
- A clear description of the problem
- Steps to reproduce
- Expected vs actual behavior
- Browser and OS if it is a frontend issue
