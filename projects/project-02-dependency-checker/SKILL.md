# Skill: Dependency Checker

> **Usage:** Checks for outdated dependencies and proposes safe updates.

---

## Project Conventions

- **Type:** Report-only loop (L1) — can upgrade to L2 for patch updates
- **Output:** Markdown report in `reports/dependency-report.md`
- **Frequency:** Daily or weekly
- **Token cost:** ~$0.05/run

## What This Loop Does

1. Checks for outdated dependencies
2. Categorizes by update type
3. Proposes safe updates
4. Writes report
5. Updates STATE.md

## What This Loop Must Never Do

- Never commit code directly
- Never update major versions without human approval
- Never skip test verification
