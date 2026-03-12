# Plan — Feature Planning

Break a feature into an implementable plan with clear tasks and risks.

**Feature to plan:** $ARGUMENTS

## Steps

1. **Understand the feature.** Parse the feature description above. If it is vague, ask one round of clarifying questions before proceeding. Think about: who benefits, what changes, what is the smallest useful version.

2. **Read current context.** Read `.claude/rules/architecture.md` and `.claude/rules/conventions.md` to understand the current system. Read the 3 most recent files in `.agents/decisions/` for relevant precedent.

3. **Break into atomic tasks.** Decompose the feature into small, ordered tasks. Each task should be completable in a single execution pass. For each task, specify:
   - What to do (concrete action)
   - Which files are affected (or need to be created)
   - Any dependencies on other tasks

4. **Identify risks and edge cases.** Consider:
   - What could break in existing functionality
   - Edge cases in user input, data, or state
   - Error handling needs
   - Performance implications
   - Security considerations

5. **Write the plan.** Save to `.agents/plans/` as `plan-YYYY-MM-DD-<short-slug>.md` with this structure:

```markdown
# Plan: <Feature Name>
Date: <today>
Status: in-progress

## Summary
<1-2 sentences on what this delivers and why it matters>

## Tasks
- [ ] Task 1: <description>
  - Files: <affected files>
- [ ] Task 2: <description>
  - Files: <affected files>
...

## Risks
- <risk 1>
- <risk 2>

## Dependencies
- <external dependencies, if any>

## Handoff Notes
<Context a future session needs to pick this up. Key decisions made, things tried, anything non-obvious.>
```

6. **Confidence score.** Assign a confidence score (1-10) for one-pass execution success. If the score is below 7, explicitly flag the areas of uncertainty — what might require iteration, clarification, or exploration.

7. **"No Prior Knowledge" test.** Review the plan as if you have never seen this codebase. Every task must be executable by someone with no prior knowledge, using only the plan content. If a task references a file, pattern, or concept without explaining where it is or what it does, add that context. If the plan fails this test, revise it before saving.

8. **Output a summary.** Show the task list, confidence score, and top risks. Confirm the plan file location.
