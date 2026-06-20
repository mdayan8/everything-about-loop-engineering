# Skill: Hello Loop

> **Usage:** Reads git history and generates a commit activity report.

---

## Project Conventions

- **Type:** Report-only loop (L1)
- **Output:** Markdown report in `reports/hello-loop-report.md`
- **Frequency:** Daily or on-demand
- **Token cost:** ~$0.01/run

## What This Loop Does

1. Reads git log for the last 30 days
2. Counts commits per author
3. Identifies most active files
4. Writes activity report
5. Updates STATE.md

## What This Loop Must Never Do

- Never modify source code
- Never create commits
- Never modify git history
