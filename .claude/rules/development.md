# Development Workflow

## Commands

<!-- Fill in your actual project commands.
Example:
  - Dev server: `npm run dev` (starts on http://localhost:3000)
  - Build: `npm run build`
  - Test: `npm test` (unit + integration)
  - Test watch: `npm test -- --watch`
  - Lint: `npm run lint`
  - Format: `npm run format`
  - Type check: `npm run typecheck`
  - Database migrate: `npm run db:migrate`
  - Database seed: `npm run db:seed`
  - Database studio: `npm run db:studio`
-->

## Environment Setup

<!-- Steps to get a new dev machine running.
Example:
  1. Clone the repo
  2. Install dependencies: `npm install`
  3. Copy environment template: `cp .env.example .env`
  4. Fill in required env vars (see below)
  5. Start database: `docker compose up -d`
  6. Run migrations: `npm run db:migrate`
  7. Seed dev data: `npm run db:seed`
  8. Start dev server: `npm run dev`
-->

## Environment Variables

<!-- List required env vars and their purpose (not their values).
Example:
  - DATABASE_URL — PostgreSQL connection string
  - AUTH_SECRET — session signing secret (generate with `openssl rand -base64 32`)
  - STRIPE_SECRET_KEY — Stripe API key (use test mode key for dev)
  - STRIPE_WEBHOOK_SECRET — Stripe webhook signing secret
  - RESEND_API_KEY — email sending service key
See .env.example for the full list with placeholder values.
-->

## Deployment

<!-- Describe how the app gets to production.
Example:
  - Push to main triggers Vercel deploy
  - Preview deploys on all PRs
  - Database migrations run automatically via CI
  - Environment variables managed in Vercel dashboard
  - Rollback: revert commit and push, or use Vercel instant rollback
-->

## Branch Strategy

<!-- Define your branching workflow.
Example:
  - main — production, always deployable
  - dev — integration branch for upcoming release
  - feature/* — individual features (branch from dev)
  - fix/* — bug fixes
  - hotfix/* — urgent production fixes (branch from main)
  - Merge via squash PR, delete branch after merge
-->

## PR Conventions

<!-- Define what a good PR looks like.
Example:
  - Title: concise description of the change
  - Description: what changed, why, how to test
  - Keep PRs small (< 400 lines diff preferred)
  - All checks must pass before merge
  - At least one approval required
  - Use /review command before requesting human review
-->

## Useful Scripts

<!-- Handy one-liners and scripts for common tasks.
Example:
  - Reset local DB: `npm run db:reset`
  - Generate API client: `npm run codegen`
  - Analyze bundle: `npm run analyze`
  - Check for outdated deps: `npm outdated`
  - Run single test: `npm test -- --grep "test name"`
-->
