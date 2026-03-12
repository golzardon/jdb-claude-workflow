# Validate — Run Configured Quality Checks

Run the project's configured validation checks in sequence. Optionally run a single check via $ARGUMENTS.

## Steps

1. Read `.claude/rules/development.md` and extract configured commands for:
   - **lint** — static analysis / linting
   - **type-check** — type checking (if applicable)
   - **test** — test suite
   - **build** — production build

2. If no commands are configured (all blank or file missing):
   - Warn: "No validation commands configured."
   - Suggest: "Fill in the lint, type-check, test, and build commands in `.claude/rules/development.md`."
   - Stop here.

3. Determine which checks to run:
   - If `$ARGUMENTS` is provided (e.g., `lint`, `test`, `type-check`, `build`), run ONLY that single check.
   - If `$ARGUMENTS` is empty, run ALL configured checks in this order: lint, type-check, test, build.
   - Skip any check that has no command configured (do not error on unconfigured optional checks).

4. For each check to run:
   - Announce: "Running [check name]..."
   - Execute the configured command.
   - If it **passes**: record as PASS and continue to the next check.
   - If it **fails**: record as FAIL, display the error output with enough context to diagnose the issue, and **stop immediately** — do not run remaining checks.

5. After all checks complete (or one fails), print a summary table:
   ```
   Validation Results:
     lint:       PASS | FAIL | SKIPPED
     type-check: PASS | FAIL | SKIPPED
     test:       PASS | FAIL | SKIPPED
     build:      PASS | FAIL | SKIPPED
   ```

6. If all checks passed, confirm: "All validations passed."
   If any check failed, confirm: "Validation failed at [check name]. Fix the errors above and re-run."

## Notes
- Do not assume any specific toolchain — commands come from development.md.
- If a command is configured but the tool is not installed, treat that as a failure and report it clearly.
- Keep output concise. Show full error output only for failures.
