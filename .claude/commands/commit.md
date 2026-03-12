# Commit — Fast, Clean Git Commit

Stage and commit changes with a well-crafted message.

> **Safety:** NEVER run `taskkill` targeting `node.exe` — Claude Code runs on Node.js.

## Steps

1. **Assess changes.** Run `git status` and `git diff --stat`. Understand what changed and why.

2. **Check commit style.** Run `git log --oneline -5` to see the repo's commit message convention. Match the style (conventional commits, imperative mood, etc.). If no history exists, use conventional commit format: `type: concise description`.

3. **Stage files.** Stage all relevant changed files. Exclude:
   - `.env`, `.env.*` files
   - Credential files, secrets, API keys
   - OS artifacts (`.DS_Store`, `Thumbs.db`)
   - Build artifacts unless they are intentionally tracked

   Use `git add <specific files>` rather than `git add -A` when sensitive files might be present.

4. **Pre-commit check.** Check `.claude/rules/development.md` for a defined build, lint, or type-check command. If one exists, run it. If it fails, fix the issue before committing. If no command is defined, skip this step entirely — do not guess at build commands.

5. **Commit.** Write a concise commit message:
   - First line: type + short summary (under 72 chars)
   - If the change is non-trivial, add a blank line then 1-2 sentences of context
   - Do not over-explain obvious changes
   - If the commit includes changes to rule files (`.claude/rules/`), documentation, or CLAUDE.md, append `[maintain]` to the commit message

6. **Quick reflection.** One question: did this work reveal a pattern, gotcha, or convention worth remembering? If yes, append a single bullet to MEMORY.md. If no, move on. This should take 5 seconds, not 5 minutes. Additionally, if this work was part of a plan (check `.agents/plans/`), save a brief execution report to `.agents/execution-reports/` noting what diverged from the plan and what was harder or easier than expected.

7. **Post-commit checks.**
   - **CLAUDE.md guardrail:** Count lines in CLAUDE.md. If it exceeds 60 lines, remind the user: "CLAUDE.md has grown to {N} lines. Consider running /maintain to extract sections into rules."
   - **Maintenance staleness:** Run `git log --grep="\[maintain\]" -1` to find the last maintenance commit. Count commits since then. If 10+ commits have passed since the last `[maintain]` commit, remind: "10+ commits since last /maintain. Consider running it."

8. **Show result.** Output the commit hash and message. If there are remaining unstaged changes, mention them.
