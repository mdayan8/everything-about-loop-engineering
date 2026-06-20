# Module 07: What Goes Wrong

> **Failure modes, cautionary examples, and a pre-flight checklist before enabling any L2+ loop.**

---

## The Short Version

Loops can fail. Some failures are obvious (the loop crashes). Some are subtle (the loop runs perfectly but produces wrong output). Some are dangerous (the loop runs perfectly, produces output that looks correct, and ships code with a security vulnerability).

This module covers the failure modes you need to understand before giving a loop any autonomy.

---

## Failure Mode 1: Verification Stays on the Human

**What happens:** The loop claims "done" but the output hasn't been independently verified. The human has to check everything the loop produces, which may be more work than doing the task manually.

**Why it's dangerous:** It creates the illusion of automation while shifting the verification burden to the human. The loop appears to save time but actually just moves the work.

**Mitigation:** Use sub-agents for independent verification. Build automated checks (tests, linting, schema validation) that the loop can run against its own output.

---

## Failure Mode 2: Comprehension Debt

**What happens:** The loop ships code faster than humans can read it. Understanding rots — nobody knows why a particular change was made, what it depends on, or what it breaks.

**Why it's dangerous:** Technical debt compounds silently. Six months later, nobody understands the codebase and the loop is the only entity that "knows" why things are the way they are.

**Mitigation:** Require the loop to write meaningful commit messages and PR descriptions. Review diffs, not just test results. Maintain architecture documentation that the loop updates.

---

## Failure Mode 3: Cognitive Surrender

**What happens:** The human accepts the loop's output without judgment. The output looks good on the surface — formatted correctly, tests pass — but contains subtle issues that require human expertise to catch.

**Why it's dangerous:** It's indistinguishable from good practice on the surface. The human reviews the output, it looks correct, and they approve it. But the review is shallow because the human trusts the loop.

**Mitigation:** Maintain active skepticism. Review loop output with the same rigor you'd apply to a junior developer's PR. Ask "what could go wrong?" not "does this look right?"

---

## Failure Mode 4: Token Cost Spikes

**What happens:** The loop's token consumption spikes unexpectedly — sub-agent fanout, infinite retry loops, or the loop processing more data than anticipated.

**Why it's dangerous:** Unexpected costs. A loop that costs $0.50/day might cost $50/day if something goes wrong.

**Mitigation:** Set hard spend caps. Monitor token usage. Use budget alerts. Start with L1 loops (minimal cost) and increase complexity gradually.

---

## Failure Mode 5: Multi-Loop Collisions

**What happens:** Two loops touch the same branch or files without coordination. One loop's changes break the other loop's assumptions. Both loops report success independently.

**Why it's dangerous:** The failures may not be immediately apparent. The loops appear to work until their changes interact in unexpected ways.

**Mitigation:** Use worktrees for isolation. Coordinate loop schedules. Define clear ownership (which loop owns which files). See [Module 09: Multi-Loop Coordination](../09-advanced-topics/multi-loop-coordination.md).

---

## Failure Mode 6: The Agent Grades Its Own Work

**What happens:** The same model that does the work also verifies it. The model's self-assessment is unreliable — it may claim success when it hasn't actually verified the output.

**Why it's dangerous:** It's the most invisible failure mode. Everything appears to work. The agent reports confidence. But the verification is shallow or absent.

**Mitigation:** Use sub-agents with a different model for verification. Build objective checks (tests pass, linting clean, schema valid) that don't rely on the model's self-assessment.

---

## Case Study: The Password Default

> **This is a real cautionary example from the loop engineering community.**

An unattended coding-agent-in-a-loop experiment shipped code with default, unchanged passwords left in place.

**What happened:**
1. The loop was configured to fix issues and ship code
2. The code included database connection strings with default passwords
3. Nothing in the loop specifically checked for default credentials
4. The loop fixed other issues successfully and shipped the changes
5. The default passwords shipped to production

**The lesson:** A loop only catches what you specifically taught it to check. If you don't include a security check in the loop's verification step, the loop will not find security issues — no matter how capable the model is.

**This is not a model failure. It's a loop design failure.** The model did exactly what it was told. The problem is that nobody told it to check for default passwords.

---

## Pre-Flight Checklist

Before enabling any L2+ loop, verify:

- [ ] **Verifier sub-agent is in place** — independent verification, not self-assessment
- [ ] **Spend cap is set** — hard limit on token consumption
- [ ] **Kill switch is tested** — you can stop the loop immediately
- [ ] **Scope is narrow enough for current tier** — one type of change, well-defined
- [ ] **Human review point is defined** — where does the human check the output?
- [ ] **Automated verification exists** — tests, linting, schema validation
- [ ] **L1 has run successfully for** — at least 1 week (L2) or 2 weeks (L3)
- [ ] **Failure modes are documented** — you know what can go wrong
- [ ] **Rollback plan exists** — you can undo the loop's changes if needed

See [templates/loop-design-checklist.md](../../templates/loop-design-checklist.md) for a printable version.

---

## The Golden Rule

> **A loop only catches what you specifically taught it to check.**

If you don't include a check, the loop won't find the issue. If you don't define "done" objectively, the loop will decide for itself when it's done. If you don't set limits, the loop will consume whatever resources it needs.

Design your loop with the assumption that it will do exactly what you told it to do — no more, no less.

---

## Try It Yourself

**Goal:** Apply the pre-flight checklist to your Changelog Drafter loop.

**Steps:**
1. Review the pre-flight checklist above.
2. For your Changelog Drafter loop, answer each question.
3. Identify any gaps (e.g., "I don't have a spend cap" or "I haven't tested the kill switch").
4. Fix the gaps before proceeding.

**Success condition:** You can check off every item on the pre-flight checklist for your loop. If any item cannot be checked, you know what needs to be addressed.

---

**Previous:** [Module 06 — Production Patterns](../06-production-patterns/README.md)
**Next:** [Module 08 — The Skeptics' Case](../08-the-skeptics-case/README.md)
