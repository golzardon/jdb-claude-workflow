# Debate — Adversarial Decision-Making

Rigorously evaluate options for a technical or product decision.

**Topic:** $ARGUMENTS

## Steps

1. **Frame the debate.** Parse the topic above. Define the core question clearly. Identify 2-4 distinct options (if not obvious from the input, propose them). If the topic is unclear, ask for clarification before proceeding.

2. **Read precedent.** Check `.agents/decisions/` for past decisions on related topics. Note any relevant constraints or patterns already established.

3. **Read current architecture.** Read `.claude/rules/architecture.md` to ground arguments in the actual system.

4. **Argue FOR each option.** For every option, make the strongest genuine case:
   - What problems does it solve well?
   - Where does it shine at scale?
   - What is the developer experience like?
   - How does it serve users?
   - What is the implementation cost (time, complexity)?

5. **Argue AGAINST each option.** For every option, attack it honestly:
   - Where does it break down?
   - What are the long-term maintenance costs?
   - What does it make harder in the future?
   - What are the hidden risks or assumptions?

6. **Evaluate tradeoffs.** Consider these dimensions explicitly:
   - Scalability
   - Maintainability
   - Developer experience
   - User impact
   - Time to implement
   - Reversibility (how hard is it to change this decision later?)

7. **Recommend.** Pick one option. State the recommendation clearly with a concise rationale. Acknowledge what you are trading away.

8. **Save the decision.** Write to `.agents/decisions/decision-YYYY-MM-DD-<short-slug>.md`:

```markdown
# Decision: <Topic>
Date: <today>
Status: accepted

## Question
<the core question>

## Options Considered
1. <option 1> — <one-line summary>
2. <option 2> — <one-line summary>
...

## Recommendation
<chosen option>

## Rationale
<why this option, 3-5 sentences>

## Tradeoffs Accepted
- <what we are giving up>

## Context
- <relevant past decisions or constraints>
```

9. **Output the recommendation** with a brief summary of the key tradeoff.
