# Incident Response Runbook

You are responding to a production incident. The incident:

**$ARGUMENTS**

Follow this structured response process. Time is critical — prioritize mitigation over root cause analysis. Save the incident record to `.agents/maintenance/incident-{date}-{short-name}.md`.

---

## Step 1: Classify Severity

Assess severity immediately based on the description:

| Level | Criteria | Response Time |
|-------|----------|---------------|
| **P0** | Service down, data loss, security breach | Immediate — drop everything |
| **P1** | Major feature broken, significant user impact | Within 1 hour |
| **P2** | Minor feature broken, workaround exists | Within 4 hours |
| **P3** | Cosmetic issue, edge case, low impact | Next business day |

State the severity level and justification.

---

## Step 2: Detect & Assess

Gather information quickly:

1. **What is broken?** Identify the specific symptoms.
2. **When did it start?** Check recent deployments, commits, and changes.
3. **Who is affected?** All users, some users, specific accounts?
4. **What changed?** Review recent commits with `git log --oneline -20` and recent deploys.

Quick triage — consult specialists if needed:
- **Security-related** (data breach, auth bypass, injection): Consult **security-engineer** agent immediately.
- **Infrastructure** (server down, DB unreachable, DNS issues): Consult **devops-automator** agent.
- **Performance** (slow responses, timeouts, memory leaks): Consult **performance-benchmarker** agent.

---

## Step 3: Investigate

Dig into the root cause:

1. **Check logs**: Look for errors, stack traces, and anomalies around the incident start time.
2. **Check monitoring**: Review metrics for the affected service — error rates, latency, resource usage.
3. **Reproduce**: Can you reproduce the issue locally? In staging?
4. **Isolate**: Narrow down to the specific component, file, or query causing the issue.
5. **Correlate**: Match the issue to a specific commit or deployment if possible.

---

## Step 4: Mitigate

Fix the immediate problem. Choose the fastest safe option:

- **Revert**: If a recent deploy caused it, revert the commit and redeploy.
- **Hotfix**: If the fix is simple and obvious, apply it directly.
- **Feature flag**: If available, disable the broken feature.
- **Workaround**: If a temporary workaround exists, communicate it to affected users.
- **Scale**: If it is a capacity issue, scale up resources.

**Rules**:
- Mitigation first, perfection later. A quick revert beats a slow fix.
- Test the mitigation in staging if possible, but don't delay if P0.
- Document what you did and why.

---

## Step 5: Verify

Confirm the fix works:

1. **Check the symptoms**: Is the original problem resolved?
2. **Monitor**: Watch error rates and performance for 15-30 minutes after the fix.
3. **Test**: Run through the affected user flow manually.
4. **Communicate**: Update stakeholders that the incident is resolved.

---

## Step 6: Post-Mortem

After the incident is resolved, create a post-mortem. Save to `.agents/maintenance/incident-{date}-{short-name}.md`.

### Post-Mortem Template

```markdown
# Incident Post-Mortem: {Short Description}

**Date**: {date}
**Severity**: {P0-P3}
**Duration**: {start time} to {resolution time}
**Impact**: {who was affected and how}

## Summary
One paragraph describing what happened.

## Timeline
- {time}: First symptoms detected
- {time}: Investigation started
- {time}: Root cause identified
- {time}: Mitigation applied
- {time}: Incident resolved

## Root Cause
What specifically caused the incident.

## Resolution
What was done to fix it.

## Lessons Learned
- What went well
- What went poorly
- Where we got lucky

## Action Items
- [ ] {Preventive measure 1}
- [ ] {Preventive measure 2}
- [ ] {Process improvement}
- [ ] {Monitoring gap to fill}
```

---

## Quick Reference

**If unsure where to start:**
1. Check `git log --oneline -10` for recent changes
2. Check application logs for errors
3. Check if the issue reproduces locally
4. If security-related, consult **security-engineer** first
5. If infra-related, consult **devops-automator** first
6. When in doubt, revert the last deploy
