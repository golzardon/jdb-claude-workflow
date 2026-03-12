# JDB-Workflow

Workflow template for full-stack SaaS development with Claude Code.

## Project Rules

See [`.claude/rules/`](.claude/rules/) — `architecture.md`, `conventions.md`, `development.md`.
Rules can use `paths:` frontmatter to only load in specific directories.

## Commands

See [`.claude/commands/`](.claude/commands/):
- `/prime` — load context | `/plan` — create a plan | `/execute` — run a plan
- `/review` — review changes | `/maintain` — sync docs | `/commit` — stage & commit
- `/create-prd` — product requirements | `/debate` — explore tradeoffs
- `/runbook-mvp` — MVP launch | `/runbook-feature` — feature delivery | `/runbook-incident` — incident response
- `/validate` — validate implementation | `/system-review` — full system review
- `/execution-report` — generate execution report | `/design-system` — design system reference
- `/refresh-handbook` — refresh project handbook | `/cost-audit` — audit costs

## Specialist Agents

See [`.claude/agents/`](.claude/agents/):
- backend-architect, security-engineer, reality-checker
- performance-benchmarker, devops-automator, growth-hacker

## Reference Docs

See [`.claude/reference/`](.claude/reference/) for large reference documents (design system, API specs, etc.).

## Reusable Skills

See [`.claude/skills/`](.claude/skills/) for reusable skill definitions (e2e-test, etc.).

## Persistent Workspace

See [`.agents/`](.agents/) for persistent artifacts:
- `plans/` — implementation plans | `decisions/` — ADRs | `reviews/` — review artifacts
- `maintenance/` — post-mortems, audits, debt tracking
- `execution-reports/` — execution report outputs
- `system-reviews/` — system review outputs

## Critical Safety Rules

- **NEVER run `taskkill` targeting `node.exe`** — Claude Code runs on Node.js.

## Notes

- **Auto-memory**: learnings saved across sessions automatically.
- **Hooks**: auto-maintenance triggers in `.claude/hooks.json`.

## Quick Start

Run `/prime` to load context and get started.
