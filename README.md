# jdb-claude-workflow

A batteries-included workflow template for [Claude Code](https://docs.anthropic.com/en/docs/claude-code) that gives you 17 slash commands, 12 specialist agents, and a self-improving feedback loop — for any tech stack.

## Why This Exists

Claude Code is powerful, but starting from scratch every session means repeating yourself. This template gives your AI assistant persistent memory, structured workflows, and specialist personas so that every session builds on the last. Plans, decisions, reviews, and learnings all survive across sessions and compound over time.

## Quick Start

```bash
# Clone the template
git clone https://github.com/golzardon/jdb-claude-workflow.git my-project
cd my-project

# Remove template history and start fresh
rm -rf .git
git init

# Open Claude Code and bootstrap
claude
# Then run:
/prime
```

That's it. The `/prime` command loads all context. The rule files in `.claude/rules/` start as commented-out templates — they fill in as you build and run `/maintain`.

> **Requires:** [Claude Code CLI](https://docs.anthropic.com/en/docs/claude-code) installed and authenticated.

## What's Inside

```
.
├── CLAUDE.md                          # Root context file (Claude reads this first)
├── .claude/
│   ├── commands/                      # 17 slash commands
│   │   ├── prime.md                   # Session startup
│   │   ├── plan.md                    # Feature planning
│   │   ├── execute.md                 # Plan execution
│   │   ├── review.md                  # Code review
│   │   ├── commit.md                  # Git commit with guardrails
│   │   ├── maintain.md                # Sync docs with code reality
│   │   ├── validate.md               # Run configured quality checks
│   │   ├── create-prd.md             # Product requirements document
│   │   ├── debate.md                  # Adversarial decision-making
│   │   ├── system-review.md           # Meta-process improvement
│   │   ├── execution-report.md        # Post-implementation reflection
│   │   ├── design-system.md           # Load UI context for frontend work
│   │   ├── refresh-handbook.md        # Generate product handbook
│   │   ├── cost-audit.md             # Infrastructure cost analysis
│   │   ├── runbook-mvp.md            # MVP launch playbook
│   │   ├── runbook-feature.md        # Enterprise feature delivery
│   │   └── runbook-incident.md       # Incident response
│   ├── agents/                        # 12 specialist personas
│   │   ├── orchestrator.md
│   │   ├── backend-architect.md
│   │   ├── security-engineer.md
│   │   ├── reality-checker.md
│   │   ├── performance-benchmarker.md
│   │   ├── devops-automator.md
│   │   ├── growth-hacker.md
│   │   ├── ux-architect.md
│   │   ├── brand-guardian.md
│   │   ├── content-creator.md
│   │   ├── seo-specialist.md
│   │   └── sprint-prioritizer.md
│   ├── rules/                         # Project rules (fill in as you build)
│   │   ├── architecture.md
│   │   ├── conventions.md
│   │   └── development.md
│   ├── reference/                     # Large reference docs
│   │   └── design-system.md
│   ├── skills/                        # Reusable skill definitions
│   │   └── e2e-test/
│   └── hooks.json                     # Auto-maintenance reminders
├── .agents/                           # Persistent workspace (survives across sessions)
│   ├── plans/                         # Implementation plans and PRDs
│   ├── decisions/                     # Architecture decision records
│   ├── reviews/                       # Code review artifacts
│   ├── execution-reports/             # Post-implementation reports
│   ├── system-reviews/                # Meta-process reviews
│   ├── maintenance/                   # Audits, post-mortems, debt tracking
│   └── skills/                        # Learned skills
└── .gitignore
```

## Core Workflow

The primary development loop:

```
  /prime ──→ /plan ──→ /execute ──→ /review ──→ /commit
     ↑                                              │
     │          /maintain (sync docs)               │
     │          /system-review (improve process)    │
     └──────────────────────────────────────────────┘
```

1. **`/prime`** — Load all project context at session start
2. **`/plan`** — Break a feature into atomic, executable tasks
3. **`/execute`** — Work through plan tasks one by one, verifying each
4. **`/review`** — Critical code review with severity ratings and auto-fix
5. **`/commit`** — Stage and commit with convention-matching messages
6. **`/maintain`** — Detect and fix drift between docs and code
7. **`/system-review`** — Compare plans vs. execution, improve the workflow itself

## Commands

| Command | Description |
|---------|-------------|
| `/prime` | Load project context and accumulated knowledge to start a session |
| `/plan` | Break a feature into an implementable plan with tasks and risks |
| `/execute` | Work through plan tasks methodically, verifying each step |
| `/review` | Security-minded code review with severity ratings and auto-fix |
| `/commit` | Stage and commit with guardrails, staleness checks, and memory |
| `/maintain` | Sync documentation and rules with actual code reality |
| `/validate` | Run configured lint, type-check, test, and build commands |
| `/create-prd` | Generate a structured product requirements document |
| `/debate` | Adversarial evaluation of technical or product decisions |
| `/system-review` | Compare plan vs. execution and propose workflow improvements |
| `/execution-report` | Post-implementation reflection capturing lessons learned |
| `/design-system` | Load or generate design system reference for UI consistency |
| `/refresh-handbook` | Generate a comprehensive product handbook from all sources |
| `/cost-audit` | Analyze infrastructure and third-party service costs |
| `/runbook-mvp` | Phased MVP launch playbook (discovery through ship) |
| `/runbook-feature` | Enterprise feature delivery from analysis to deploy |
| `/runbook-incident` | Structured incident response with severity classification |

## Agent Personas

| Agent | Specialty |
|-------|-----------|
| **orchestrator** | Meta-agent that coordinates specialists and sequences work |
| **backend-architect** | System design, data flow, service boundaries, failure modes |
| **security-engineer** | Threat modeling, vulnerability assessment, defense in depth |
| **reality-checker** | Final quality gate — verifies claims with evidence, not trust |
| **performance-benchmarker** | Measures and optimizes performance with data, not guesses |
| **devops-automator** | CI/CD, infrastructure, deployment automation |
| **growth-hacker** | User acquisition, activation, retention experiments |
| **ux-architect** | Design systems, accessibility, component hierarchies |
| **brand-guardian** | Brand consistency across visual, verbal, and experiential touchpoints |
| **content-creator** | Copy and content — landing pages, emails, microcopy |
| **seo-specialist** | Technical and content SEO, crawlability, search visibility |
| **sprint-prioritizer** | Prioritization balancing value, risk, capacity, and strategy |

Agents are invoked automatically by runbooks and commands when specialist input is needed, or you can consult them directly.

## Self-Improving Loop

This workflow gets better the more you use it:

1. **`/execute`** builds features and notes what was harder or easier than expected
2. **`/execution-report`** captures divergences from the plan and lessons learned
3. **`/system-review`** compares plans against execution, classifies divergences as "good" (justified) or "bad" (avoidable), performs root-cause analysis, and proposes concrete changes to commands, rules, or process
4. **`/maintain`** syncs all documentation with the actual codebase, removing drift
5. **`/commit`** tracks staleness and reminds you when maintenance is overdue
6. **Hooks** trigger auto-reminders when rule files are edited

The result: your commands get sharper, your rules get more accurate, and your plans get more realistic over time.

## Customization

This template is **stack-agnostic**. The rule files start as commented-out templates:

- **`.claude/rules/architecture.md`** — Define your project structure, tech stack, data flow, and API conventions
- **`.claude/rules/conventions.md`** — Define naming, error handling, logging, testing, and code organization standards
- **`.claude/rules/development.md`** — Define dev commands, environment setup, deployment, and branch strategy

As you build and run `/maintain`, these fill in with your actual patterns. You can also:

- Add new commands in `.claude/commands/` (any `.md` file becomes a `/command`)
- Add new agents in `.claude/agents/`
- Add new rules in `.claude/rules/` (use `paths:` frontmatter to scope rules to specific directories)
- Add reference docs in `.claude/reference/` for large context files
- Add reusable skills in `.claude/skills/`

## Credits

Inspired by [agency-agents](https://github.com/msitarzewski/agency-agents) by Mike Sitarzewski. The specialist agent personas are generalized from that project's original agent definitions.

## License

MIT
