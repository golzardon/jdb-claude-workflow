# Refresh Handbook — Generate Comprehensive Product Handbook

Build a stakeholder-friendly handbook covering the product, architecture, features, and workflow.

## Steps

1. **Gather all sources:**
   - Read `CLAUDE.md` (project root) if it exists.
   - Read all files in `.claude/rules/`.
   - Read all plans from `.agents/plans/`.
   - Read all decision records from `.agents/decisions/` (if directory exists).
   - Read any existing handbook at `.agents/handbook.md` for context on what changed.
   - Scan `package.json`, `pyproject.toml`, `Cargo.toml`, `go.mod`, or equivalent for dependencies and project metadata.

2. **Analyze the codebase for supplementary info:**
   - Identify the tech stack from dependencies and file types.
   - Identify entry points and main modules.
   - Look for API routes, endpoints, or service definitions.
   - Look for database schemas or models.

3. **Generate the handbook with these sections:**

   ### Product Overview
   What the product is, who it serves, and its core purpose. Keep it to 2-4 sentences.

   ### Architecture Summary
   High-level architecture: major components, how they connect, data flow. Use plain language, not implementation details.

   ### Key Features
   List each feature with a 1-2 sentence description of what it does and how it works from a user perspective.

   ### Technical Stack
   Table of technologies, frameworks, and services used, with their role in the project.

   ### Dependencies & Services
   Third-party services, APIs, databases, and external dependencies. Note which are required vs. optional.

   ### Development Workflow
   How to set up, develop, test, and deploy. Pull from rules and CLAUDE.md.

   ### Key Decisions & Rationale
   Summarize decisions from `.agents/decisions/`. For each: what was decided, why, and what alternatives were rejected.

   ### API Documentation
   If the project has an API: list endpoints, methods, and brief descriptions. If no API, omit this section.

   ### Known Limitations & Technical Debt
   Any known issues, deferred work, or architectural constraints worth noting.

4. **Save the handbook:**
   - Write to `.agents/handbook.md`, overwriting any previous version.

5. **Report completion:**
   - Print a summary of what sections were generated.
   - Note any sections that were thin due to missing source material.
   - Suggest: "Review the handbook and fill in any gaps. Re-run `/refresh-handbook` after major changes."

## Notes
- Write for a mixed audience: developers, stakeholders, and new team members should all find it useful.
- Do not dump raw code into the handbook. Summarize and explain.
- If the project is very early stage and lacks most source material, generate what you can and mark sections as "TBD."
- This command is idempotent — safe to re-run at any time to update the handbook.
