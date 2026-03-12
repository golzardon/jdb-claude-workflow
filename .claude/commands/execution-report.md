# Execution Report — Post-Implementation Self-Reflection

Document what was built, how it compared to the plan, and capture lessons learned.

## Steps

1. **Determine the subject:**
   - If `$ARGUMENTS` is provided, use it as the feature/task name.
   - If not, read the most recent plan from `.agents/plans/` and use its title/subject.
   - If neither is available, ask: "What feature or task should this report cover?"

2. **Review what was built:**
   - Run `git log --oneline -20` to see recent commits.
   - Run `git diff --stat HEAD~10` (or appropriate range) to see scope of changes.
   - Identify the files changed, added, or removed.
   - Summarize the work in 3-5 bullet points.

3. **Load the corresponding plan (if one exists):**
   - Search `.agents/plans/` for a plan matching the feature/task name.
   - If found, read it and use it for comparison in the next step.
   - If not found, note "No plan found — reporting on execution only."

4. **Write the report with these sections:**

   ### Summary
   One paragraph describing what was implemented.

   ### Completed vs. Planned
   A checklist comparing planned items against what was actually delivered.
   Mark each as: DONE, PARTIAL, SKIPPED, or UNPLANNED (for items not in the original plan).

   ### Divergences from Plan
   For each divergence, explain:
   - What diverged
   - Why it diverged (deliberate decision, discovered blocker, time constraint, etc.)

   ### Harder Than Expected
   What took more effort than anticipated and why.

   ### Easier Than Expected
   What went smoother than anticipated and why.

   ### What I Would Do Differently
   Concrete changes to approach if doing this again.

   ### Technical Debt Introduced
   Any shortcuts taken, TODOs left behind, known issues deferred.
   Rate severity: low / medium / high.

5. **Save the report:**
   - Create `.agents/execution-reports/` directory if it does not exist.
   - Save as `.agents/execution-reports/YYYY-MM-DD-[feature-name].md`.

6. **Suggest next step:**
   - Print: "Execution report saved. Run `/system-review` to analyze divergences and improve the workflow."

## Notes
- Be candid. This report is for process improvement, not status reporting.
- Focus on what can be learned, not on justifying decisions.
- If there is no git history (e.g., planning-only work), adapt and report based on file changes or conversation context instead.
