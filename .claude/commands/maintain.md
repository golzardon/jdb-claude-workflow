# Maintain — Sync Documentation with Code Reality

Detect and fix drift between documentation/rules and the actual codebase.

## Steps

1. **Read all rules.** Read every file in `.claude/rules/` — architecture.md, conventions.md, development.md, and any others present.

2. **Analyze the actual codebase.** Examine:
   - Project structure (directories, key files)
   - Tech stack and dependencies (package files, config files)
   - Code patterns actually in use (naming, structure, error handling)
   - Any configuration or infrastructure files

3. **Identify drift.** Compare rules to reality. Look for:
   - Rules that reference files, patterns, or tools that no longer exist
   - Conventions the codebase has evolved past
   - Missing rules for patterns that have become standard in the code
   - Outdated stack or dependency references
   - Architecture rules that do not match the actual structure

4. **Propose and apply updates.** For each piece of drift:
   - Explain what is out of date and what reality is
   - Propose the specific edit
   - Apply the update after confirmation (or apply non-controversial fixes directly)

5. **CLAUDE.md guardrail.** Count lines in CLAUDE.md. If it exceeds 60 lines, extract detailed sections into `.claude/rules/` files (e.g., move a detailed conventions section to `.claude/rules/conventions.md`), leaving only short pointers in CLAUDE.md. When creating new rule files, note that they can use frontmatter to scope when they load — for example, `paths: ["backend/**"]` will only load the rule when working in the backend directory. Then, if the project structure, key commands, or workflow have changed, update CLAUDE.md to reflect current reality.

6. **Review .agents/ artifacts.** Scan plans, decisions, and reviews in `.agents/`. Flag any that reference outdated patterns. Do not delete old artifacts — just note them as outdated if relevant.

7. **Review memory.** Read MEMORY.md. Flag any bullets that are no longer accurate or relevant. Remove or update stale entries.

8. **Save maintenance report.** Write a report to `.agents/maintenance/maintenance-YYYY-MM-DD.md`:

```markdown
# Maintenance Report — <date>

## Changes Made
- <what was updated and why>

## Drift Detected
- <any drift not yet resolved, with reasoning>

## Memory Updates
- <any memory entries added, updated, or removed>

## Health Assessment
<1-2 sentences on overall documentation health>
```

9. **Commit with [maintain] tag.** When committing maintenance changes, include `[maintain]` in the commit message (e.g., `docs: update rules and fix drift [maintain]`). This allows `/commit` to track staleness and remind users when maintenance is overdue.

10. **Output summary.** List what was changed and any items that need human decision.
