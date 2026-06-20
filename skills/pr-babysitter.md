# Skill: PR Babysitter

> **Usage:** Monitors open pull requests for review readiness, CI status, merge conflicts, and staleness.

---

## Project Conventions

- **Type:** Report-only loop (L1) or advisory (L2)
- **Output:** Markdown report in `reports/pr-status.md`
- **Frequency:** Every 5–15 minutes
- **Token cost:** High (~$0.50–$2.00/run)

## What This Loop Does

1. Lists all open pull requests
2. For each PR, checks:
   - CI status (are all checks passing?)
   - Review status (are required reviews approved?)
   - Merge conflicts (are there any?)
   - Age (how many days open?)
3. Flags PRs needing attention
4. Writes status report
5. Updates STATE.md

## What This Loop Must Never Do (L1)

- **Never merge PRs** — watch only
- **Never approve PRs** — watch only
- **Never request changes** — watch only
- **Never modify source code** — reads only

## What This Loop Can Do (L2, with human review)

- **Auto-approve** minor PRs (dependency bumps, formatting)
- **Request review** from assigned reviewers
- **Comment** with CI status summary

## Prompt Template (L1)

```markdown
You are a PR monitoring agent. Check the status of all open 
pull requests and report findings.

## Instructions

1. List all open PRs
2. For each PR, check:
   - CI status (passing/failing/pending)
   - Review status (approved/changes requested/pending)
   - Merge conflicts (yes/no)
   - Age (days since opened)
3. Flag PRs that need attention:
   - Failing CI
   - Changes requested
   - Merge conflicts
   - Stale (7+ days, no activity)
4. Write report to reports/pr-status.md
5. Update STATE.md

## Rules (L1)
- Do NOT merge any PRs
- Do NOT approve any PRs
- Do NOT request changes
- Do NOT modify source code
- Only read from GitHub and write to reports/ and STATE.md
```

## Verification Condition

A file exists at `reports/pr-status.md` containing:
- Count of open PRs
- Status of each PR (CI, reviews, conflicts, age)
- At least one flagged item if any PRs need attention

## Cost Optimization

- Start with 15-minute intervals
- Only reduce to 5 minutes if 15 minutes misses time-sensitive issues
- Consider using GitHub webhooks instead of polling for real-time updates
- Use a smaller model (haiku) for status checks, larger model (sonnet) only for analysis
