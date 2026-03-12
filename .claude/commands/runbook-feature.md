# Enterprise Feature Runbook

You are executing a structured feature delivery plan for a significant new feature. The feature:

**$ARGUMENTS**

This runbook is for features that are too large or impactful for a simple plan-and-execute. Follow the phases below. Save the execution plan to `.agents/plans/feature-{feature-name}.md`.

---

## Phase 1: Analysis

**Goal**: Fully understand the feature and its impact before writing code.

1. **Scope definition**: What exactly does this feature do? What does it NOT do? Write a clear one-paragraph description.

2. **Impact analysis**: Identify what existing code and systems this feature touches:
   - Which files and modules will be modified?
   - Which database tables need changes?
   - Which API endpoints are affected?
   - Are there breaking changes for existing users?

3. **Architecture consultation**: Consult the **backend-architect** agent to:
   - Propose a design that fits the existing architecture
   - Identify potential scaling concerns
   - Recommend data model changes
   - Flag any architectural risks

4. **Dependencies**: List external dependencies, third-party services, or prerequisites.

**Deliverables**: Scope doc, impact analysis, architecture recommendation.

---

## Phase 2: Plan

**Goal**: Create a detailed, sprint-ready implementation plan.

1. **Run `/plan`**: Break the feature into concrete implementation steps. Each step should be:
   - Small enough to complete in one session
   - Testable independently
   - Ordered by dependency (build foundations first)

2. **Key decisions**: For any non-obvious technical choices, run `/debate` to explore options. Save decisions to `.agents/decisions/`.

3. **Risk mitigation**: Identify what could go wrong and plan for it:
   - Data migration risks
   - Backward compatibility concerns
   - Performance implications
   - Security considerations (consult **security-engineer** if relevant)

4. **Test plan**: Define what tests are needed before starting the build:
   - Unit tests for new business logic
   - Integration tests for new API endpoints
   - E2E tests for new user flows
   - Regression tests for existing features that might break

**Deliverables**: Step-by-step plan, decision records, risk register, test plan.

---

## Phase 3: Build

**Goal**: Implement the feature in manageable sprints.

Execute the plan in sprints of 3-5 steps each:

1. **Sprint execution**: Run `/execute` for each sprint batch.
2. **Sprint review**: After each sprint, run `/review` to check:
   - Code quality and consistency with conventions
   - Test coverage for new code
   - No regressions in existing functionality
   - Performance characteristics

3. **Course correction**: If the plan needs adjustment based on discoveries during build, update the plan before continuing.

**Build order**:
- Database migrations and data layer changes first
- Backend logic and API endpoints second
- Frontend UI and integration third
- Tests throughout (not at the end)

**Checkpoints**:
- After data layer: verify migrations work both up and down
- After API: verify with manual testing or API client
- After UI: verify full user flow works end to end

**Deliverables**: Working feature with tests, updated per sprint review feedback.

---

## Phase 4: Verify

**Goal**: Confirm the feature is production-ready.

1. **Reality check**: Consult the **reality-checker** agent to audit:
   - Edge cases and error handling
   - Missing validation
   - Accessibility concerns
   - Mobile responsiveness (if applicable)

2. **Performance**: Consult the **performance-benchmarker** agent to:
   - Benchmark new endpoints and queries
   - Compare against baseline performance
   - Identify any degradation

3. **Security review**: If the feature handles user data, auth, or payments, consult the **security-engineer** agent.

4. **Run full test suite**: Ensure no regressions.

**Deliverables**: Audit results, performance benchmarks, security sign-off, green test suite.

---

## Phase 5: Ship

**Goal**: Deploy safely and monitor.

1. **Commit**: Run `/commit` with a clear description of the feature.

2. **Deploy strategy**: Determine rollout approach:
   - Feature flag for gradual rollout?
   - Direct deploy?
   - Blue-green deployment?

3. **Monitor**: After deploy, watch for:
   - Error rate changes
   - Performance degradation
   - User-reported issues
   - Database query performance

4. **Documentation**: Update relevant docs:
   - `.claude/rules/architecture.md` if architecture changed
   - `.claude/rules/development.md` if new commands or processes
   - API documentation if endpoints changed

**Deliverables**: Deployed feature, monitoring confirmed, docs updated.

---

## Tracking

Save execution status to `.agents/plans/feature-{feature-name}.md`:
- [ ] Phase 1: Analysis
- [ ] Phase 2: Plan
- [ ] Phase 3: Build
- [ ] Phase 4: Verify
- [ ] Phase 5: Ship
