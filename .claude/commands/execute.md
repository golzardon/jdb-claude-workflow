# Execute — Implement Tasks from a Plan

Work through plan tasks methodically, verifying each step.

**Input:** $ARGUMENTS

## Steps

1. **Find the plan.** If arguments are provided, treat them as either a task description (ad-hoc work) or a plan file reference. If no arguments, look in `.agents/plans/` for the most recent plan with status `in-progress`. If no plan is found, ask what to work on.

2. **Identify the next incomplete task.** Find the first unchecked task (`- [ ]`) in the plan.

3. **Execute the task.** Implement it fully:
   - Write the code or make the changes
   - Follow conventions from `.claude/rules/conventions.md`
   - Follow architecture patterns from `.claude/rules/architecture.md`

4. **Verify the task.** After implementation, do a quick sanity check:
   - Does the code have obvious errors or typos?
   - If there is a build/run command defined in the project rules, run it
   - If tests exist for the affected area, run them
   - If verification fails, fix the issue before moving on

5. **Mark the task complete.** Update the plan file — change `- [ ]` to `- [x]` for the completed task.

6. **Repeat.** Go to step 2 for the next task. Continue until all tasks are done or you hit a blocker.

7. **Handle blockers.** If something unexpected happens or a task cannot be completed:
   - Note the blocker in the plan file under Handoff Notes
   - Move to the next unblocked task if possible
   - Report the blocker clearly

8. **Wrap up.** When all tasks are done (or you have completed a meaningful chunk):
   - Update the plan status to `complete` if all tasks are done
   - Do a quick reflection: did anything unexpected happen? Did you discover a pattern, gotcha, or shortcut? If yes, append it to MEMORY.md as a concise bullet under the appropriate section. If nothing notable, skip this — do not force it.
   - Output a brief summary of what was completed and any open items.
