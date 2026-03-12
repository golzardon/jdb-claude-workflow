# Coding Conventions

> Fill in as you establish patterns. /maintain will help keep this current.

## Naming Conventions

<!-- Define naming rules for consistency.
Example:
  - Files: kebab-case (user-profile.ts, auth-service.ts)
  - Variables/functions: camelCase
  - Classes/types/interfaces: PascalCase
  - Constants: UPPER_SNAKE_CASE
  - Components: PascalCase matching filename (UserProfile.tsx)
  - Database tables: snake_case plural (user_profiles)
  - Database columns: snake_case (created_at)
  - Environment variables: UPPER_SNAKE_CASE with prefix (APP_DATABASE_URL)
-->

## Error Handling

<!-- Define how errors are handled consistently.
Example:
  - Use custom error classes extending a base AppError
  - Always include error code, message, and optional context
  - Never expose internal errors to clients
  - Log full error with stack trace server-side
  - Return user-friendly message client-side
  - Use Result<T, E> pattern for expected failures
-->

## Logging Standards

<!-- Define what, when, and how to log.
Example:
  - Use structured JSON logging in production
  - Log levels: error (broken), warn (degraded), info (notable), debug (dev only)
  - Always include: timestamp, request_id, user_id (if available)
  - Never log secrets, tokens, passwords, or PII
  - Use a shared logger instance, not console.log
-->

## Testing Conventions

<!-- Define your testing approach.
Example:
  - Unit tests for all business logic (services, utilities)
  - Integration tests for API routes and database queries
  - E2E tests for critical user flows (signup, payment, core feature)
  - Test file placement: colocated (*.test.ts next to source)
  - Naming: describe('ServiceName') > it('should do specific thing')
  - Mocking: mock external services, use real DB for integration
-->

## Code Organization

<!-- Define how code is organized within files and modules.
Example:
  - One export per file for components and services
  - Group by feature, not by type (feature/ not components/, services/)
  - Shared utilities in lib/ with barrel exports
  - Keep files under 300 lines; extract when larger
  - Colocate related files (component + test + styles + types)
-->

## Import Ordering

<!-- Define import order for readability.
Example:
  1. External packages (react, next, etc.)
  2. Internal aliases (@/lib, @/components)
  3. Relative imports (./utils, ../shared)
  4. Type imports (import type { ... })
  5. Style imports
  Blank line between each group. Alphabetize within groups.
-->
