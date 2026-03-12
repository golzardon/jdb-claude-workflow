# Architecture Rules

> Update this file as the project evolves. Run /maintain to sync with code reality.

## Project Structure

<!-- Define your top-level directory layout here.
Example:
  src/
    app/        — Next.js app router pages
    lib/        — shared utilities and helpers
    components/ — UI components
    services/   — business logic and external integrations
  infra/        — IaC and deployment configs
  tests/        — test suites
-->

## Tech Stack & Key Dependencies

<!-- List your core technologies and why they were chosen.
Example:
  - Runtime: Node.js 20 LTS
  - Framework: Next.js 14 (app router)
  - Database: PostgreSQL 16 via Supabase
  - Auth: Supabase Auth (magic link + OAuth)
  - Payments: Stripe
  - Hosting: Vercel (app) + Supabase (db/auth)
-->

## Architecture Pattern

<!-- Describe the overall system shape.
Example:
  Monolithic Next.js app with API routes. Server components for data fetching,
  client components for interactivity. Edge middleware for auth checks.
  Background jobs via Inngest.
Options: monolith, microservices, serverless, modular monolith, event-driven, etc.
-->

## Data Flow

<!-- Describe how data moves through the system.
Example:
  Browser → Edge Middleware (auth) → Server Component → Database
  Mutations: Client → Server Action → Service Layer → Database
  Background: Event → Queue → Worker → Database
-->

## Database Design Principles

<!-- Define your data modeling approach.
Example:
  - Use UUIDs for all primary keys
  - Soft deletes via deleted_at timestamp
  - Row-level security policies on all tables
  - Migrations managed via Prisma / Drizzle / raw SQL
  - Audit trail on sensitive tables
-->

## API Design Conventions

<!-- Define your API patterns.
Example:
  - REST with consistent resource naming: /api/v1/{resource}
  - Always return { data, error, meta } shape
  - Use HTTP status codes correctly (201 for creation, 404 for missing, etc.)
  - Rate limiting on all public endpoints
  - Versioned via URL path
-->

## Key Architectural Decisions

<!-- Link to decision records as they are made.
Example:
  - [ADR-001: Chose Next.js over Remix](.agents/decisions/adr-001-nextjs.md)
  - [ADR-002: PostgreSQL over MongoDB](.agents/decisions/adr-002-postgres.md)
See .agents/decisions/ for the full archive.
-->
