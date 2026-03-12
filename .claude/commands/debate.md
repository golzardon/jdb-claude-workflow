---
description: "Debate whether a feature or decision should be implemented"
argument-hint: <feature-request-or-decision-topic>
---

# Feature / Decision Debate

Run a structured deliberation to evaluate whether a proposed feature, request, or technical decision should be implemented. Uses a "Rubric-First Analyst/Critic" pattern to avoid forced-stance argumentation.

**Topic:** $ARGUMENTS

---

## Step 0 — Gather Context

Before analysis, collect the context needed:

1. Read `CLAUDE.md` (project overview, priorities, current phase)
2. Read `.claude/rules/architecture.md` (system structure, stack, patterns)
3. Read any other relevant rules in `.claude/rules/`
4. Check `.agents/decisions/` for past decisions on related topics — note any relevant constraints or patterns already established
5. Skim any files directly relevant to the proposed feature/decision (use Glob/Grep to find them)

Hold this context — you will reference it throughout the analysis.

---

## Step 1 — Define the Evaluation Rubric

Act as an impartial **evaluation judge**. Create a **weighted evaluation rubric** to assess this feature/decision. Do NOT evaluate it yet — just define the scoring criteria.

Generate a rubric with 5-7 criteria. For each criterion:
- Name and description (1 sentence)
- Weight (1-10, must sum to a reasonable total)
- What a high score (8-10) looks like
- What a low score (1-3) looks like

Always include these core criteria (adjust weights based on the topic):
1. **Strategic Alignment** — Does this align with the project's vision and current priorities?
2. **User Value** — How much does this improve the user experience? Is there demand signal?
3. **Technical Feasibility** — Can this be built cleanly within the current architecture?
4. **Cost & Effort** — Development time, infrastructure, COGS, and maintenance cost implications?
5. **Scope & Risk** — Is scope well-defined? Risk of creep or unforeseen complexity?
6. **Reversibility** — How hard is it to undo or change this decision later?

You may add 1-2 additional criteria if the topic warrants them (e.g., "Competitive Advantage", "Revenue Impact", "Compliance", "Time Sensitivity", "Developer Experience").

Define a decision threshold:
- **IMPLEMENT**: weighted score >= 70%
- **MODIFY**: weighted score 50-69% (implement with specified changes)
- **DEFER**: weighted score 30-49% (revisit later with specified conditions)
- **REJECT**: weighted score < 30%

---

## Step 2 — Analyst Assessment

Act as a **senior product/engineering analyst**. Provide a comprehensive, honest analysis. You are NOT an advocate — if the feature is bad, say so.

For each rubric criterion:
- Your assessment (with specific evidence/reasoning grounded in the project's actual codebase and constraints)
- Suggested score (1-10)

Then provide:
- **Benefits** — What value does this deliver? Be specific.
- **Costs** — Development effort, infrastructure impact, maintenance burden. Estimate where possible.
- **Risks** — What could go wrong? Technical debt? User confusion?
- **Alternatives** — Are there simpler ways to achieve the same goal?
- **Implementation sketch** — High-level approach if implemented (2-3 sentences max)

Be thorough and evidence-based. Cite specific project constraints (architecture patterns, current phase, cost targets) when relevant.

---

## Step 3 — Critic Assessment

Now switch perspective. Act as a **devil's advocate and stress-tester**. Find the **strongest possible objections**. A feature that survives this scrutiny is stronger for it. Do NOT soften the critique.

For each rubric criterion:
- Your most critical assessment (assume worst-case where reasonable)
- Suggested score (1-10)

Then provide:
- **Hidden costs** — What will this ACTUALLY cost beyond the obvious? Second-order effects?
- **Opportunity cost** — What are we NOT building by building this? What's more important?
- **Scope creep risks** — How will this expand beyond initial spec? What adjacent requests will it trigger?
- **Failure modes** — How could this fail in production? Edge cases? Misuse?
- **Simpler alternatives** — Could we achieve 80% of the value with 20% of the effort?
- **Pre-mortem** — "It's 3 months later and this was a mistake. Why?" Write 2-3 plausible failure narratives.

Be genuinely adversarial. Surface what the analyst might miss or underweight.

---

## Step 4 — Judge Deliberation

Return to the impartial **judge** perspective. Score the feature/decision against the rubric, informed by both the analyst and critic assessments.

For each rubric criterion:
- Final score (1-10) with 1-sentence justification
- Whether the analyst or critic made the stronger point on this criterion

Calculate the weighted total score and percentage.

Determine the verdict: **IMPLEMENT** / **MODIFY** / **DEFER** / **REJECT**

Write 2-3 paragraphs of reasoning explaining the decision. Address the strongest argument from each perspective. Be decisive — do not hedge with "it depends."

If MODIFY or DEFER, specify the exact changes or conditions required.

List 1-3 concrete recommended next steps regardless of verdict.

---

## Step 5 — Present Results

Display the final output in this format:

```
## Debate: [topic name]

### Rubric
| Criterion | Weight | Analyst | Critic | Final | Justification |
|-----------|--------|---------|--------|-------|---------------|
| ...       | ...    | ...     | ...    | ...   | ...           |

**Weighted Score: [X]%**

### Analyst Summary
- [2-3 bullet points — key arguments]

### Critic Summary
- [2-3 bullet points — key objections]

### Verdict: [IMPLEMENT/MODIFY/DEFER/REJECT] ([score]%)
[Judge's reasoning — 2-3 paragraphs]

### Conditions
[If MODIFY or DEFER — specific changes or conditions required]

### Recommended Next Steps
[1-3 concrete actions]
```

---

## Step 6 — Save Decision Record

Write the decision to `.agents/decisions/decision-YYYY-MM-DD-<short-slug>.md`:

```markdown
# Decision: <Topic>
Date: <today>
Status: accepted
Verdict: <IMPLEMENT/MODIFY/DEFER/REJECT> (<score>%)

## Question
<the core question debated>

## Options Considered
1. <option 1> — <one-line summary>
2. <option 2> — <one-line summary>
...

## Recommendation
<chosen option or verdict>

## Rationale
<why this verdict, 3-5 sentences>

## Tradeoffs Accepted
- <what we are giving up>

## Key Risks
- <top risks identified by critic>

## Conditions (if any)
- <changes or conditions required before implementation>

## Context
- <relevant past decisions or constraints>
```
