# MVP Launch Runbook

You are executing a structured MVP launch plan. The project goal:

**$ARGUMENTS**

Follow this phased playbook to go from idea to launched product. Save the execution plan to `.agents/plans/mvp-runbook.md` as you go, updating status on each phase.

---

## Phase 1: Discovery + Architecture (Week 1)

**Goal**: Validate the idea, define scope, and lock in architecture.

1. **Create PRD**: Run `/create-prd` with the project description to generate a product requirements document. Save to `.agents/plans/prd.md`.

2. **Define MVP scope**: Identify the smallest set of features that delivers value. Ruthlessly cut nice-to-haves. List:
   - Must-have features (launch blockers)
   - Should-have features (fast follows)
   - Won't-have features (future)

3. **Architecture decisions**: For each major technical choice, run `/debate` to explore tradeoffs. Consult the **backend-architect** agent for system design. Save decisions to `.agents/decisions/`.
   - Runtime and framework
   - Database and data layer
   - Authentication approach
   - Hosting and deployment
   - Payment processing (if applicable)

4. **Update rules**: Fill in `.claude/rules/architecture.md` with the chosen stack and patterns.

**Deliverables**: PRD, scoped feature list, architecture decisions, filled-in architecture rules.

---

## Phase 2: Core Build (Weeks 2-3)

**Goal**: Build the core features that make the product useful.

For each feature in priority order:

1. **Plan**: Run `/plan` to break the feature into implementation steps.
2. **Execute**: Run `/execute` to build it step by step.
3. **Review**: Run `/review` after completing each feature.

**Key features to build in order**:
- Project scaffolding and dev environment
- Database schema and data layer
- Authentication and user management (consult **security-engineer** agent)
- Core feature #1 (the thing that makes this product unique)
- Core feature #2
- Basic UI/UX for the above

**Checkpoints**:
- After auth: consult **security-engineer** for review
- After each feature: run `/review` for code quality
- End of week 3: working prototype with core flows

**Deliverables**: Working prototype with auth, core features, and basic UI.

---

## Phase 3: Polish + Hardening (Week 4)

**Goal**: Make it production-ready.

1. **Reality check**: Consult the **reality-checker** agent to audit the codebase for:
   - Missing error handling
   - Hardcoded values
   - Security gaps
   - Missing tests

2. **Performance**: Consult the **performance-benchmarker** agent to:
   - Identify slow queries
   - Check for N+1 problems
   - Verify caching strategy
   - Load test critical paths

3. **Testing**: Write tests for critical paths:
   - Auth flows (signup, login, logout, password reset)
   - Payment flows (if applicable)
   - Core feature happy paths
   - Key error scenarios

4. **UI polish**: Fix rough edges, loading states, error states, empty states.

**Deliverables**: Test suite, performance baseline, polished UI, fixed audit findings.

---

## Phase 4: Launch Prep (Weeks 5-6)

**Goal**: Ship it and get first users.

1. **Infrastructure**: Consult the **devops-automator** agent to:
   - Set up CI/CD pipeline
   - Configure production environment
   - Set up monitoring and alerting
   - Configure backups
   - Set up error tracking

2. **Launch checklist**:
   - [ ] Production environment configured
   - [ ] Domain and DNS set up
   - [ ] SSL certificate active
   - [ ] Environment variables set in production
   - [ ] Database migrations applied
   - [ ] Monitoring and alerts active
   - [ ] Error tracking configured
   - [ ] Backup strategy verified
   - [ ] Legal pages (privacy policy, terms) added
   - [ ] Analytics installed

3. **Growth**: Consult the **growth-hacker** agent for:
   - Landing page optimization
   - Launch channel strategy
   - Initial user acquisition plan
   - Feedback collection mechanism

4. **Ship**: Deploy to production, announce, monitor closely for 48 hours.

**Deliverables**: Live product, monitoring dashboard, launch announcement, feedback pipeline.

---

## Tracking

Save this execution plan to `.agents/plans/mvp-runbook.md` with status tracking:
- [ ] Phase 1: Discovery + Architecture
- [ ] Phase 2: Core Build
- [ ] Phase 3: Polish + Hardening
- [ ] Phase 4: Launch Prep

Update status as each phase completes. Log blockers and decisions along the way.
