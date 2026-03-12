# Create PRD — Product Requirements Document

Generate a structured, actionable PRD for a feature or product idea.

**Feature/Idea:** $ARGUMENTS

## Steps

1. **Understand the idea.** Parse the input above. If critical details are missing (who is this for? what problem does it solve?), ask up to 3 clarifying questions before proceeding.

2. **Read context.** Read `.claude/rules/architecture.md` to understand current technical capabilities and constraints. Check `.agents/plans/` for any existing PRDs or related plans to avoid duplication and maintain consistency.

3. **Generate the PRD.** Write a structured document covering:

   **Problem Statement** — What problem exists? Who has it? Why does it matter? Ground this in user needs, not implementation desire.

   **Target Users** — Who specifically benefits? What is their context?

   **Success Metrics** — How do we know this worked? Define 2-4 measurable outcomes.

   **Requirements**
   - Must-have: the minimum set for this to be useful
   - Nice-to-have: valuable additions that can be deferred
   - Out of scope: explicitly call out what this is NOT

   **Technical Considerations** — Based on the current architecture, what are the key technical factors? Integration points, data model changes, infrastructure needs. Keep this grounded in the actual codebase, not hypothetical.

   **Risks & Open Questions** — What could go wrong? What needs more research? What assumptions are we making?

   **Timeline Estimate** — Rough t-shirt size (small/medium/large) with brief justification. Break into phases if the feature is large.

4. **Save the PRD.** Write to `.agents/plans/prd-YYYY-MM-DD-<short-slug>.md` using this format:

```markdown
# PRD: <Feature Name>
Date: <today>
Status: draft
Author: AI-assisted

## Problem Statement
<2-4 sentences>

## Target Users
<who and their context>

## Success Metrics
- <metric 1>
- <metric 2>

## Requirements

### Must-Have
- <requirement>

### Nice-to-Have
- <requirement>

### Out of Scope
- <explicitly excluded>

## Technical Considerations
<grounded in current architecture>

## Risks & Open Questions
- <risk or question>

## Timeline Estimate
<t-shirt size + phases if applicable>
```

5. **Output a summary.** Show the problem statement, must-have requirements, and top risks. Confirm the file location. Suggest running `/plan` next to break it into implementable tasks.
