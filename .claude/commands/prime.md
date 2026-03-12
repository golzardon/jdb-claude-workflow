# Prime — Session Startup

Load project context and accumulated knowledge to start a productive session.

## Steps

1. **Read project context.** Read CLAUDE.md at the project root. Then read all files in `.claude/rules/` (architecture.md, conventions.md, development.md). Internalize the key constraints and patterns — do not recite them back.

2. **Read auto-memory.** Read MEMORY.md at the project root. Read any files in `.agents/maintenance/` from the last 7 days. These contain hard-won learnings — pay attention to gotchas, patterns, and warnings.

3. **Check recent decisions.** Read the 3 most recent files in `.agents/decisions/`. Note any architectural direction or constraints they establish.

4. **Check recent git history.** Run `git log --oneline -15` to understand recent momentum. Note what areas of the codebase have been active.

5. **Check for in-progress work.** Look in `.agents/plans/` for any plans that have incomplete tasks. If found, summarize what was in progress and what remains.

6. **Surface a brief status report.** Output a concise summary:
   - What this project is and its current state (1-2 sentences)
   - Any known issues or gotchas from memory
   - In-progress work that needs attention (if any)
   - Suggested next action (if there's unfinished work, suggest picking it up)

Keep the output short and actionable. The goal is context loading, not a dissertation.
