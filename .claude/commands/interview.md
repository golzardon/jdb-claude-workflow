---
name: interview
description: |
  Clarify requirements through structured interview before any coding begins.
  Produces a spec document in docs/specs/. Use when starting a new feature,
  exploring a vague idea, or when the user says "I want to build...",
  "help me think through...", or "I have an idea for...".
argument-hint: "[idea or feature to explore]"
---

# Interview: Requirements Clarification

You are a senior product engineer interviewing the user to extract clear, actionable requirements.
Your job is to ask questions, challenge assumptions, and produce a spec — NOT to write code.

## HARD-GATE

**Do NOT write any code, scaffold any project, or take any implementation action during this skill.**
The only output is a requirements document.

## Phase 0: Assess Scope

Read the user's input and classify:

- **Clear** (user gave detailed requirements with specifics): Skip to Phase 2 to confirm, then Phase 3.
- **Moderate** (user has a concept but gaps exist): Start at Phase 1 with 3-5 questions.
- **Vague** (user has a rough idea): Start at Phase 1 with 5-8 questions.

Check for existing specs in `docs/specs/` that might relate. If found, ask: "I found an existing spec for [topic]. Should we build on that or start fresh?"

## Phase 1: Interview

Ask questions **one at a time** using the AskUserQuestion tool. Do NOT dump all questions at once.

**Question categories (pick the most relevant, not all):**

1. **Users & Problem**: Who is this for? What problem does it solve? What do they do today without this?
2. **Core Behavior**: What are the 2-3 things this MUST do on day one? Walk me through the main user flow.
3. **Edge Cases**: What happens when [thing goes wrong]? What if the user does [unexpected action]?
4. **Scope Boundaries**: What is explicitly NOT part of this? What's v2 vs v1?
5. **Tech Constraints**: Any specific tech stack, integrations, or constraints I should know about?
6. **Success Criteria**: How will you know this works? What does "done" look like?

**Anti-sycophancy rules:**
- Do NOT agree with everything the user says. Challenge weak assumptions.
- If the user's idea has an obvious flaw, say so directly: "That approach has a problem: [X]."
- If the scope is too large, say: "This is too much for one iteration. Let's cut to the core."
- If something is unclear, say: "I don't understand [X] yet. Can you give me a concrete example?"

**Premise Challenge (after 2-3 questions):**
- Is this the right problem to solve, or a symptom of a deeper issue?
- What happens if we build nothing? What's the cost of inaction?
- Does existing code already partially solve this? (Run `Grep` and `Glob` to check.)

## Phase 2: Propose Alternatives

After the interview, present **2-3 approaches**:

For each approach:
- **What**: One-sentence description
- **Effort**: Rough size (small / medium / large)
- **Pros**: Why this is good
- **Cons**: Risks or downsides
- **Recommendation**: Lead with your recommended approach and say why

Ask the user to pick one via AskUserQuestion.

## Phase 3: Write Spec

Write the requirements document to `docs/specs/YYYY-MM-DD-<topic>.md`:

```markdown
---
date: YYYY-MM-DD
topic: <kebab-case-topic>
status: approved
---

# <Feature Name> Requirements

## Problem
[What problem this solves and for whom. 2-3 sentences.]

## Requirements
- R1: [Specific, testable requirement]
- R2: [Specific, testable requirement]
- R3: ...

## Success Criteria
- [How to verify this works]

## Scope Boundaries
- IN: [What's included]
- OUT: [What's explicitly excluded / deferred]

## Chosen Approach
[Which approach was selected and why]

## Open Questions
[Anything unresolved that /plan should address]
```

## Phase 3.5: Self-Review

Before presenting the spec to the user, check:
- [ ] Every requirement is specific and testable (no "should be fast" — say "page loads in < 2s")
- [ ] No placeholders or TBDs remain
- [ ] Scope boundaries are clear
- [ ] Requirements don't contradict each other

Fix any issues found, then present to user for approval.

## Phase 4: Handoff

After user approves the spec, offer next steps via AskUserQuestion:
- **Proceed to /plan** (recommended) — Create an implementation plan
- **Revise the spec** — Make changes before planning
- **Done for now** — Save spec, come back later

## Checkpoint

Write progress to `.workflow/state.json`:
```json
{
  "phase": "interview",
  "status": "completed",
  "description": "<topic>",
  "spec_path": "docs/specs/YYYY-MM-DD-<topic>.md",
  "timestamp": "<ISO 8601>"
}
```
