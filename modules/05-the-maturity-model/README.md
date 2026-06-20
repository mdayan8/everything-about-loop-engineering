# Module 05: The Maturity Model

> **L1, L2, L3 — three tiers of loop autonomy, and when to advance from one to the next.**

---

## The Short Version

Not all loops are equal. Some just read and report. Some propose changes. Some commit and deploy autonomously. The maturity model defines three tiers and tells you which tier to use for what.

| Tier | Name | What It Does | When to Use |
|------|------|-------------|-------------|
| **L1** | Report Only | Reads, observes, writes down — changes nothing | Most loops, most of the time |
| **L2** | Assisted / Patch-Only | Proposes narrow-scope changes; human merges | When L1 is proven and the scope is tight |
| **L3** | Unattended | Commits, merges, deploys autonomously inside guardrails | Rarely. Few tasks earn this. |

---

## L1 — Report Only

The loop runs, finds things, writes them down, and changes nothing. The human reads the output and decides what to do.

**Example:** A daily triage loop that reads open issues, categorizes them, and writes a summary. It doesn't close issues, doesn't assign them, doesn't change any code.

**Why L1 matters:** L1 is the foundation. It's where you prove the loop works, where you build trust in its output, and where you learn what it actually does before giving it more power.

**Advice:** Most loops should stay at L1 far longer than feels necessary. L1 is not a stepping stone — it's a destination. Many tasks never need to go beyond L1.

### When L1 Is Sufficient

- Monitoring and reporting (triage, audits, summaries)
- Anything where a human needs to make the final decision
- Early-stage loops where you're still learning what the loop should do
- Any task where the cost of a wrong action is high

---

## L2 — Assisted / Patch-Only

The loop proposes narrow-scope changes: dependency bumps, lint fixes, changelog drafts, formatting improvements. A human still reviews and merges every change.

**Example:** A dependency sweeper that proposes updating a package from version 1.2.3 to 1.2.4. It opens a PR, runs tests, and waits for human review.

**Why L2 matters:** L2 is where loops start saving real time. The loop does the boring work (find outdated deps, check compatibility, open a PR), and the human does the judgment work (should we actually upgrade this?).

**Advice:** Only move to L2 after L1 has been running successfully for a meaningful period. "Successfully" means: the output is consistently accurate, the scope is proven narrow, and the failure modes are understood.

### When L2 Is Appropriate

- The task is narrow-scope (one type of change, well-defined)
- L1 has been running successfully for at least a week
- The human review step is genuinely quick (not a full audit)
- The cost of a wrong change is low and reversible

---

## L3 — Unattended

The loop commits, merges, or deploys on its own, inside guardrails already proven at L1 and L2. This is full autonomy — the loop runs without human intervention.

**Example:** A post-merge cleanup loop that automatically formats code, updates generated documentation, and pushes the changes directly.

**Why L3 matters:** L3 is where loops reach their theoretical maximum value — fully autonomous, no human in the loop. But it's also where the risk is highest.

**Advice:** Few tasks ever earn L3. The bar should be extremely high:
- L1 has been running successfully for weeks/months
- L2 has been running successfully for weeks/months
- The task is narrow and well-understood
- The cost of a wrong change is minimal and reversible
- Automated verification (sub-agents, tests) catches errors before they reach production

### When L3 Is Appropriate

- Formatting and style changes (reversible, low-impact)
- Documentation updates from structured data (auto-generated, verifiable)
- Dependency updates with full test suite verification
- Tasks where the verification step is provably reliable

---

## The Readiness Rubric

Use this to decide whether to advance a loop:

| Criterion | L1→L2 | L2→L3 |
|-----------|--------|--------|
| L1 has run successfully for | ≥ 1 week | ≥ 2 weeks |
| L2 has run successfully for | N/A | ≥ 2 weeks |
| Output is consistently accurate | Yes | Yes |
| Scope is narrow and well-defined | Yes | Yes |
| Failure modes are understood | Yes | Yes |
| Automated verification exists | Recommended | Required |
| Cost of wrong change is | Low | Minimal and reversible |
| Human review time is | Minutes, not hours | N/A (no human review) |

**If any criterion is not met, stay at the current tier.**

---

## The Rollout Advice

> Most loops should stay at L1 far longer than feels necessary. Few tasks ever earn L3.

This is not pessimism. It's based on the observation that:
- L1 loops are nearly free and nearly riskless
- L2 loops require genuine human attention for review
- L3 loops require provably reliable automated verification
- The jump from L1 to L2 is larger than it looks
- The jump from L2 to L3 is enormous

When in doubt, stay at the current tier longer.

---

## Try It Yourself

**Goal:** Assess whether your Changelog Drafter loop (from Module 04) is ready to advance.

**Steps:**
1. Review the readiness rubric above.
2. For your Changelog Drafter loop, answer each criterion honestly.
3. If all L1→L2 criteria are met, consider adding a sub-agent to verify the draft.
4. If any criterion is not met, identify what needs to happen before advancing.

**Success condition:** You have a clear, evidence-based assessment of your loop's current tier and a plan for what needs to happen before advancing (or a decision to stay at L1).

---

**Previous:** [Module 04 — Building Your First Loop](../04-building-your-first-loop/README.md)
**Next:** [Module 06 — Production Patterns](../06-production-patterns/README.md)
