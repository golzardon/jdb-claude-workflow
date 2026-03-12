# Skill: End-to-End Testing

## When to Use
Use this skill for end-to-end testing of user-facing flows — signup, checkout, dashboards, forms, or any multi-step interaction a real user would perform.

## Prerequisites
- Check `.claude/rules/development.md` for the configured test command and framework (Playwright, Cypress, etc.)
- Identify the test directory convention from the project structure

## Workflow

### 1. Identify the Flow
Determine what to test from the arguments or conversation context. Examples: "user signup," "payment checkout," "settings page."

### 2. Research the Implementation
- Read the relevant route/page/component files for the flow
- Identify API endpoints, form fields, navigation paths, and expected states
- Note any loading states, error boundaries, or redirects

### 3. Write Test Cases
Cover these categories for each flow:

**Happy Path** — The standard successful journey from start to finish.

**Error States** — Invalid inputs, network failures, permission denied, expired sessions.

**Edge Cases** — Empty states, maximum input lengths, rapid repeated submissions, back-button navigation.

**Accessibility** — Keyboard navigation, screen reader labels, focus management, ARIA attributes.

### 4. Run the Tests
```bash
# Use the test command from development.md, e.g.:
# npx playwright test <test-file>
# npx cypress run --spec <test-file>
```

### 5. Analyze and Fix Failures
- Read the error output carefully
- Check for flaky selectors (prefer `data-testid`, roles, or accessible names over CSS classes)
- Fix timing issues with proper waits (never use arbitrary sleep)
- Re-run until green

### 6. Visual Verification (Browser-Based)
If the framework supports it, capture screenshots at key states for visual verification.

## Test Organization
- Name test files: `<flow-name>.e2e.test.{ts,js}` or `<flow-name>.spec.{ts,js}`
- Group related assertions in `describe`/`test.describe` blocks
- Use descriptive test names: `"should show error when email is invalid"`
- Keep tests independent — each test should set up and tear down its own state

## Notes
- The actual test framework and run command must be configured in `.claude/rules/development.md`
- Prefer testing user-visible behavior over implementation details
- Use fixtures and factories for test data, not hardcoded values
