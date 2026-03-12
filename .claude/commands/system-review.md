# System Review — Meta-Process Improvement

Compare plans against execution, identify divergences, and improve the workflow itself. This is the self-improving feedback loop.

## Steps

1. **Load the most recent plan:**
   - List files in `.agents/plans/` and read the most recently modified plan.
   - If no plans exist, report: "No plans found in `.agents/plans/`. Run `/plan` first." and stop.

2. **Load the most recent execution report:**
   - List files in `.agents/execution-reports/` and read the most recently modified report.
   - If no execution reports exist, note this gap and suggest running `/execution-report` first. Continue with a plan-only review.

3. **Compare plan vs. execution:**
   - Identify each planned item and whether it was completed, partially completed, or missed.
   - Identify anything that was done but NOT in the plan.
   - Note any timeline or scope differences.

4. **Classify divergences into two categories:**

   **Good divergences** — justified improvements discovered during execution:
   - Found a better approach than planned
   - Addressed an issue discovered mid-implementation
   - Reasonable scope adjustment based on new information

   **Bad divergences** — avoidable problems:
   - Missed requirements that were clearly stated
   - Scope creep without justification
   - Avoidable mistakes or rework

5. **Root-cause analysis for bad divergences:**
   For each bad divergence, determine the root cause:
   - **Bad plan**: plan was unrealistic, underspecified, or wrong
   - **Unclear requirements**: ambiguity led to wrong interpretation
   - **Missing context**: needed information was not available at planning time
   - **Tooling issue**: process or tools failed to catch the problem

6. **Suggest concrete workflow improvements:**
   Based on the root causes, propose specific changes:
   - Command file edits (better prompts, additional steps)
   - New rules to add to `.claude/rules/`
   - Memory entries to add for future context
   - Process changes (e.g., "always run /validate before completing a feature")
   - Template improvements

7. **Offer to apply improvements:**
   - List each proposed change and ask if the user wants to apply it.
   - For approved changes, edit the relevant files directly.

8. **Save the review:**
   - Save to `.agents/system-reviews/YYYY-MM-DD-review.md` with structured sections:
     - Plan summary
     - Execution summary
     - Good divergences
     - Bad divergences with root causes
     - Improvement proposals
     - Applied changes

9. **Run `/maintain`** at the end to sync documentation with any changes made.

## Notes
- Be honest and specific in the analysis. Vague observations like "could be better" are useless.
- Focus on systemic fixes, not one-off issues. If a problem could recur, propose a process change.
- This command is the engine that makes the whole workflow get better over time. Treat it seriously.
