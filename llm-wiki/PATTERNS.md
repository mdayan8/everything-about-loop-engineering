# LLM Wiki: Production Patterns

> Six battle-tested loop patterns with configurations, costs, and maturity guidance.

---

## Pattern Selection Guide

| Your Biggest Pain Point | Start With | Pattern |
|------------------------|------------|---------|
| "I don't know what needs attention" | Daily Triage | L1, low cost |
| "PRs sit unreviewed for days" | PR Babysitter | L1, high cost |
| "CI keeps breaking and nobody notices" | CI Sweeper | L2, very high cost |
| "Dependencies are outdated and vulnerable" | Dependency Sweeper | L2, medium cost |
| "Changelogs are always incomplete" | Changelog Drafter | L1, low cost |
| "Codebase gets messy after merges" | Post-Merge Cleanup | L1, low cost |

**Start with Changelog Drafter or Daily Triage.** Lowest risk, lowest cost, immediate value.

---

## Daily Triage

**What it does:** Reads open issues, PRs, and recent activity. Categorizes by priority, labels, and assignee status. Writes a summary report.

**Cadence:** Once daily (morning recommended)
**Starting maturity:** L1
**Token cost:** Low (~$1.50–$6.00/month)

**Config (GitHub Actions):**
```yaml
name: Daily Triage
on:
  schedule:
    - cron: '0 9 * * *'
  workflow_dispatch:
jobs:
  triage:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - run: claude --prompt-file prompts/triage.md --state-file STATE.md
```

**Prompt file contents:**
```markdown
You are a triage agent. Read all open issues and PRs.
Categorize by: urgent, normal, low priority.
Flag anything stale (7+ days no activity).
Write summary to reports/triage.md.
Update STATE.md.
Rules: Do NOT close issues. Do NOT assign people. Do NOT merge PRs.
```

**Success condition:** `reports/triage.md` exists with categorized items.

---

## PR Babysitter

**What it does:** Monitors open pull requests for: review readiness, CI status, merge conflicts, stale PRs.

**Cadence:** Every 5–15 minutes
**Starting maturity:** L1 (watch only)
**Token cost:** High (~$15–$60/month)

**Config:**
```yaml
name: PR Babysitter
on:
  schedule:
    - cron: '*/15 * * * *'
jobs:
  watch:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - run: claude --prompt-file prompts/pr-watch.md --state-file STATE.md
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

**Caution:** High token cost. Start with 15-minute intervals. Only reduce if value is proven.

---

## CI Sweeper

**What it does:** Checks CI build status across all active branches. Identifies flaky tests, failing builds, performance regressions.

**Cadence:** Every 5–15 minutes
**Starting maturity:** L2 (cautious — proposes fixes, human merges)
**Token cost:** Very high

**Caution:** Highest-risk, highest-cost pattern. Requires proven L1 monitoring first. Only move to L2 after monitoring loop has been accurate for weeks.

---

## Dependency Sweeper

**What it does:** Checks for outdated dependencies. Proposes updates with changelogs and compatibility notes. Runs tests to verify.

**Cadence:** Every 6 hours to once daily
**Starting maturity:** L2 (patch-only)
**Token cost:** Medium (~$6–$24/month)

**Config:**
```yaml
name: Dependency Sweeper
on:
  schedule:
    - cron: '0 */6 * * *'
jobs:
  sweep:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - run: claude --prompt-file prompts/deps.md --state-file STATE.md --approval-mode suggest
```

**Rules:** Only auto-commit patch updates (1.2.3 → 1.2.4). Minor: propose, don't commit. Major: flag for human.

---

## Changelog Drafter

**What it does:** Reads git history, categorizes commits by type, drafts a changelog. Changes nothing.

**Cadence:** Daily or per-release
**Starting maturity:** L1 (draft)
**Token cost:** Low (~$1.50–$4.50/month)

**This is the recommended first loop.** See [../modules/04-building-your-first-loop/README.md](../modules/04-building-your-first-loop/README.md) for the full walkthrough.

**Prompt file contents:**
```markdown
You are a changelog drafter. Read git log for last 30 days.
Categorize commits: feat, fix, docs, chore, refactor, test, perf, ci.
Write draft to reports/changelog-draft.md.
Update STATE.md.
Rules: Do NOT modify code. Do NOT create commits.
```

**Success condition:** `reports/changelog-draft.md` exists with categorized commits.

---

## Post-Merge Cleanup

**What it does:** After a PR is merged, runs cleanup: formatting, updating generated docs, removing dead code, running linters with auto-fix.

**Cadence:** Every 1–6 hours (or triggered by merge events)
**Starting maturity:** L1 (off-peak — reports what needs cleanup)
**Token cost:** Low

**Caution:** Start with report-only. Only enable auto-fix for truly safe operations (formatting, linting) after extensive L1 validation.

---

## Cost Comparison

| Pattern | Daily Cost | Monthly Cost | Token Usage |
|---------|-----------|-------------|-------------|
| Daily Triage (L1) | $0.05–$0.20 | $1.50–$6.00 | Low |
| Changelog Drafter (L1) | $0.05–$0.15 | $1.50–$4.50 | Low |
| Post-Merge Cleanup (L1) | $0.05–$0.15 | $1.50–$4.50 | Low |
| Dependency Sweeper (L2) | $0.20–$0.80 | $6.00–$24.00 | Medium |
| PR Babysitter (L1) | $0.50–$2.00 | $15.00–$60.00 | High |
| CI Sweeper (L2) | $1.00–$5.00 | $30.00–$150.00 | Very high |

*Estimates based on typical usage. Actual costs depend on model, context size, and task complexity.*

---

*See [FAILURE-MODES.md](FAILURE-MODES.md) for what goes wrong. See [../templates/](../templates/) for fill-in-the-blank configs.*
