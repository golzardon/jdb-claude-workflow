# Prime — Session Startup

Load project context and accumulated knowledge to start a productive session.

## Steps

### Step 0: Detect first session

Before loading context, determine if this is the first session or a returning session:

- Check if `MEMORY.md` exists at the project root
- Check if `.claude/rules/architecture.md` has been filled in (contains actual content beyond the empty template headings)

**If this is a FIRST session** (no memory file, or architecture rules are empty):

1. **Map the project structure.** Run `git ls-files` (or `tree -L 3 --dirsfirst` if not a git repo) to understand the codebase layout.

2. **Read main entry points.** Look for and read key entry files:
   - `main.py`, `app.py`, `index.ts`, `index.js`, `main.ts`, `main.go`, `src/main.rs`, `server.py`, `server.ts`
   - `src/index.*`, `src/app.*`, `src/main.*`
   - Read whichever exist — these reveal the app's structure and wiring

3. **Read core config files.** Look for and read:
   - `package.json`, `tsconfig.json` (Node/TS projects)
   - `pyproject.toml`, `requirements.txt`, `setup.py` (Python projects)
   - `Cargo.toml` (Rust), `go.mod` (Go), `Gemfile` (Ruby)
   - `.env.example` or `.env.local` (environment variables — never `.env` itself)
   - `docker-compose.yml`, `Dockerfile` if they exist

4. **Read README.** If `README.md` exists, read it for project overview and setup instructions.

5. **Identify tech stack and patterns.** From what you read, identify:
   - Language(s) and framework(s)
   - Database(s) and ORM(s)
   - Authentication approach
   - API style (REST, GraphQL, tRPC, etc.)
   - Frontend framework and state management
   - Key architectural patterns (monorepo, microservices, serverless, etc.)

6. **Suggest initialization.** Tell the user: "This looks like a first session. Consider running `/init` to auto-populate the project rules in `.claude/rules/`."

7. **Output a "First time here" project overview:**
   - What this project is and does
   - Tech stack summary
   - Key directories and their purposes
   - Entry points and how the app starts
   - Suggested areas to explore or next steps

Then stop — do not continue to the returning session steps.

---

**If this is a RETURNING session** (memory exists and rules are populated), continue with the steps below:

### Step 1: Read project context

Read CLAUDE.md at the project root. Then read all files in `.claude/rules/` (architecture.md, conventions.md, development.md). Internalize the key constraints and patterns — do not recite them back.

### Step 2: Read auto-memory

Read MEMORY.md at the project root. Read any files in `.agents/maintenance/` from the last 7 days. These contain hard-won learnings — pay attention to gotchas, patterns, and warnings.

### Step 3: Check recent decisions

Read the 3 most recent files in `.agents/decisions/`. Note any architectural direction or constraints they establish.

### Step 4: Check recent git history

Run `git log --oneline -15` to understand recent momentum. Note what areas of the codebase have been active.

### Step 5: Check for in-progress work

Look in `.agents/plans/` for any plans that have incomplete tasks. If found, summarize what was in progress and what remains.

### Step 6: Surface a brief status report

Output a concise summary:
- What this project is and its current state (1-2 sentences)
- Any known issues or gotchas from memory
- In-progress work that needs attention (if any)
- Suggested next action (if there's unfinished work, suggest picking it up)

Keep the output short and actionable. The goal is context loading, not a dissertation.
