# Execute — Implement Tasks from a Plan

Work through plan tasks methodically, front-loading context and verifying each step before moving on. Thoroughness over speed.

**Input:** $ARGUMENTS

## Steps

### Phase 1: Load Plan & Context

1. **Find the plan.** If arguments are provided, treat them as either a task description (ad-hoc work) or a plan file reference. If no arguments, look in `.agents/plans/` for the most recent plan with status `in-progress`. If no plan is found, ask what to work on.

2. **Read all context references.** Before writing any code, read ALL files listed in the plan:
   - Every file under "Relevant Codebase Files" — understand existing patterns, types, and conventions in use
   - Every file under "Relevant Documentation" — understand requirements and constraints
   - `.claude/rules/conventions.md` and `.claude/rules/architecture.md` — internalize project standards
   - If the plan references other plans or ADRs, read those too
   - This step is non-negotiable. Skipping it leads to code that contradicts existing patterns.

3. **Identify the next incomplete task.** Find the first unchecked task (`- [ ]`) in the plan.

### Phase 2: Execute Tasks (repeat for each task)

4. **Execute the task.** Implement it fully:
   - Write the code or make the changes
   - Follow conventions from `.claude/rules/conventions.md`
   - Follow architecture patterns from `.claude/rules/architecture.md`
   - Match the style and patterns observed in the context files read in step 2

5. **Validate the task immediately.** Do not batch validation to the end:
   - If the plan specifies a VALIDATE command for this task, run it now
   - Does the code have obvious errors or typos?
   - If there is a build/run command defined in the project rules, run it
   - If tests exist for the affected area, run them
   - If validation fails, fix the issue before moving on — do not proceed with a broken task

6. **Mark the task complete.** Update the plan file — change `- [ ]` to `- [x]` for the completed task.

7. **Repeat.** Go to step 3 for the next task. Continue until all implementation tasks are done or you hit a blocker.

### Phase 3: Handle Blockers

8. **Handle blockers.** If something unexpected happens or a task cannot be completed:
   - Note the blocker in the plan file under Handoff Notes
   - Move to the next unblocked task if possible
   - Report the blocker clearly

### Phase 4: Testing Strategy

9. **Implement the testing strategy.** After all implementation tasks are complete, execute the testing strategy from the plan:
   - Create test files as specified in the plan
   - Implement all test cases listed (unit, integration, edge cases)
   - Cover edge cases and error scenarios the plan calls out
   - Run the full test suite and fix any failures before proceeding
   - If the plan has no testing section, write tests for the critical paths you implemented

### Phase 5: Full Validation

10. **Run all validation commands from the plan.** Execute them in order (Level 1 through Level 5 if specified):
    - Level 1: Type checking, linting
    - Level 2: Unit tests
    - Level 3: Integration tests
    - Level 4: Build verification
    - Level 5: End-to-end or manual checks
    - Fix any failures at each level before proceeding to the next

11. **Final verification checklist.** Confirm all of the following before wrapping up:
    - [ ] All tasks in the plan are marked `[x]`
    - [ ] All tests pass (new and existing)
    - [ ] All validation commands pass
    - [ ] Code follows project conventions (naming, error handling, imports)
    - [ ] No regressions in existing functionality
    - [ ] No leftover TODOs, debug logs, or commented-out code

### Phase 6: Wrap Up

12. **Update plan status.** Set the plan status to `complete` if all tasks are done.

13. **Memory reflection.** Did anything unexpected happen? Did you discover a pattern, gotcha, or shortcut? If yes, append it to MEMORY.md as a concise bullet under the appropriate section. If nothing notable, skip this — do not force it.

14. **Output the execution report.** Provide a structured summary:

```
## Execution Report

### Completed Tasks
- Task 1: <description> — <files touched>
- Task 2: <description> — <files touched>

### Files Created
- <path> — <purpose>

### Files Modified
- <path> — <what changed>

### Tests Added
- <test file> — <n> test cases — <pass/fail>

### Validation Results
- Level 1 (lint/types): PASS/FAIL
- Level 2 (unit tests): PASS/FAIL
- Level 3 (integration): PASS/FAIL
- Level 4 (build): PASS/FAIL

### Deviations from Plan
- <any deviations and why, or "None">

### Status: Ready for `/commit`
```
