# LLM Wiki: Failure Modes

> What goes wrong with loops, why it happens, and how to prevent it.

---

## The Golden Rule

> **A loop only catches what you specifically taught it to check.**

If you don't include a check, the loop won't find the issue. If you don't define "done" objectively, the loop will decide for itself. If you don't set limits, the loop will consume whatever resources it needs.

---

## Failure Mode 1: Verification Stays on the Human

**What happens:** Agent claims "done" but output hasn't been independently verified. Human has to check everything — may be more work than doing the task manually.

**Why it's dangerous:** Creates illusion of automation while shifting verification burden to human.

**Example:** A loop that "fixes bugs" but the human still has to read every diff, run every test, and check every edge case. The loop saved no time.

**Prevention:**
- Use sub-agents for independent verification
- Build automated checks (tests, linting, schema validation)
- Define objective success criteria the loop can check itself

---

## Failure Mode 2: Comprehension Debt

**What happens:** Code ships faster than humans can read it. Nobody knows why a change was made, what it depends on, or what it breaks.

**Why it's dangerous:** Technical debt compounds silently. Six months later, nobody understands the codebase.

**Example:** A loop merges 50 PRs in a week. Each passes tests. But nobody read the diffs. The codebase is now incomprehensible.

**Prevention:**
- Require meaningful commit messages and PR descriptions
- Review diffs, not just test results
- Maintain architecture documentation the loop updates
- Cap the number of changes per loop run

---

## Failure Mode 3: Cognitive Surrender

**What happens:** Human accepts loop output without judgment. Output looks correct on the surface but contains subtle issues.

**Why it's dangerous:** Indistinguishable from good practice on the surface. The human reviews, it looks correct, they approve. But the review is shallow.

**Example:** A loop produces a well-formatted, test-passing PR. The human glances at it and merges. The PR introduces a subtle race condition that only manifests under load.

**Prevention:**
- Maintain active skepticism
- Review loop output with the same rigor as a junior developer's PR
- Ask "what could go wrong?" not "does this look right?"
- Rotate who reviews loop output

---

## Failure Mode 4: Token Cost Spikes

**What happens:** Token consumption spikes unexpectedly — sub-agent fanout, infinite retry loops, or processing more data than anticipated.

**Why it's dangerous:** A loop that costs $0.50/day might cost $50/day if something goes wrong.

**Example:** A loop with 3 sub-agents enters a retry cycle. Each retry spawns 3 more sub-agents. Token usage grows exponentially until the budget is exhausted.

**Prevention:**
- Set hard spend caps (daily and per-run)
- Monitor token usage with alerts
- Use budget limits at the API level
- Start with L1 (minimal cost) and increase complexity gradually
- Set max_turns on every agent

---

## Failure Mode 5: Multi-Loop Collisions

**What happens:** Two loops touch the same branch or files without coordination. One loop's changes break the other's assumptions.

**Why it's dangerous:** Failures may not be apparent immediately. Loops appear to work until changes interact.

**Example:** PR Babysitter approves a PR. Dependency Sweeper updates a dependency in the same file. Both succeed independently. The merged result breaks the build.

**Prevention:**
- Use worktrees for isolation
- Define file-level ownership (which loop owns which files)
- Coordinate schedules (don't run conflicting loops simultaneously)
- Use branch naming conventions (loop/pr-babysitter/1234)

---

## Failure Mode 6: The Agent Grades Its Own Work

**What happens:** Same model does the work and verifies it. Self-assessment is unreliable — may claim success without actual verification.

**Why it's dangerous:** Most invisible failure mode. Everything appears to work. Agent reports confidence. Verification is shallow or absent.

**Example:** A loop "runs tests" but the agent reads the test file and reports "tests pass" without actually executing them. No human checks.

**Prevention:**
- Use sub-agents with a different model for verification
- Build objective checks that don't rely on model self-assessment
- Require proof (test output, CI logs) not claims
- Use goal-condition primitives

---

## Case Study: The Password Default

> Self-reported from the loop engineering community.

An unattended coding-agent-in-a-loop shipped code with default, unchanged passwords left in place.

**What happened:**
1. Loop configured to fix issues and ship code
2. Code included database connection strings with default passwords
3. Nothing in the loop checked for default credentials
4. Loop fixed other issues successfully and shipped changes
5. Default passwords shipped to production

**Lesson:** The loop did exactly what it was told. The problem is that nobody told it to check for default passwords. A loop only catches what you specifically taught it to check.

---

## Pre-Flight Checklist

Before enabling any L2+ loop:

- [ ] **Verifier sub-agent is in place** — independent verification
- [ ] **Spend cap is set** — hard limit on token consumption
- [ ] **Kill switch is tested** — you can stop the loop immediately
- [ ] **Scope is narrow** — one type of change, well-defined
- [ ] **Human review point is defined** — where does human check output?
- [ ] **Automated verification exists** — tests, linting, schema validation
- [ ] **L1 has run successfully for** — at least 1 week (L2) or 2 weeks (L3)
- [ ] **Failure modes are documented** — you know what can go wrong
- [ ] **Rollback plan exists** — you can undo the loop's changes

---

*See [PATTERNS.md](PATTERNS.md) for production patterns. See [../templates/loop-design-checklist.md](../templates/loop-design-checklist.md) for the printable checklist.*
