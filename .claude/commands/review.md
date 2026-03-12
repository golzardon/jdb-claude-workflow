# Review — Critical Code Review

Review code with a security-minded, quality-focused perspective.

**Scope:** $ARGUMENTS

## Steps

1. **Determine scope.** Parse the input:
   - `last commit` or `latest` → review the last commit (`git diff HEAD~1`)
   - A file path → review that specific file
   - `staged` or no input → review staged changes (`git diff --cached`)
   - A directory path → review all files in that directory
   - A PR number or branch → diff against main/master

2. **Read conventions.** Read `.claude/rules/conventions.md` and `.claude/rules/architecture.md` to know what standards to enforce.

3. **Review the code.** Examine every change with a critical eye. Check for:

   **Bugs & Logic Errors**
   - Off-by-one errors, null/undefined access, race conditions
   - Incorrect control flow, missing return statements
   - Type mismatches or implicit coercions

   **Security (OWASP Top 10 focus)**
   - Injection vulnerabilities (SQL, XSS, command injection)
   - Broken authentication or authorization checks
   - Sensitive data exposure (secrets, PII in logs)
   - Missing input validation or sanitization

   **Performance**
   - N+1 queries, unbounded loops, missing pagination
   - Unnecessary re-renders, expensive operations in hot paths
   - Missing caching where appropriate

   **Error Handling**
   - Swallowed errors, missing try/catch, unhelpful error messages
   - Missing edge case handling
   - Inconsistent error patterns

   **Code Quality**
   - Violations of project conventions
   - Dead code, duplicated logic
   - Unclear naming, missing context
   - Overly complex functions that should be split

4. **Rate each finding.** Assign severity:
   - **CRITICAL** — Must fix. Bugs, security holes, data loss risks.
   - **WARNING** — Should fix. Performance issues, error handling gaps, maintainability concerns.
   - **SUGGESTION** — Consider fixing. Style, naming, minor improvements.

5. **Output the review.** Format findings clearly:
   ```
   [CRITICAL] file.ext:L42 — Description of issue
   [WARNING] file.ext:L87 — Description of issue
   [SUGGESTION] file.ext:L15 — Description of issue
   ```
   If no issues found, say so explicitly — but double-check first. Be genuinely critical.

6. **Fix mode.** If critical or warning issues were found:
   - Present each fixable issue and offer to fix it immediately.
   - For each fix applied, re-verify the fix by re-reading the affected code to confirm the issue is resolved and no new issues were introduced.
   - After all fixes are applied, do a final pass over the changed files to catch any regressions.
   - The user should not need a separate command to fix review findings — this command handles both review and fix in one pass.

7. **Save the review.** Write to `.agents/reviews/review-YYYY-MM-DD-<scope-slug>.md`:

```markdown
# Code Review — <scope>
Date: <today>

## Summary
<1-2 sentences: overall quality assessment>

## Findings
<all findings with severity, location, description>

## Stats
- Critical: <n>
- Warnings: <n>
- Suggestions: <n>
```

8. **Memory check.** If the review revealed a recurring issue or pattern worth flagging in future reviews, save it to MEMORY.md.
