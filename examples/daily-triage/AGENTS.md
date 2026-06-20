# Agent Rules: Daily Triage

> House rules for the triage agent.

---

## Code Style

- Output is always Markdown
- Use consistent heading levels (H2 for categories, H3 for items)
- Include counts: "12 open issues (3 urgent, 5 normal, 4 low)"

## Git Conventions

- This loop does not create commits
- This loop does not create branches
- This loop writes only to reports/ and STATE.md

## Before Every Run

- [ ] GITHUB_TOKEN is set and valid
- [ ] GITHUB_REPO is set correctly
- [ ] STATE.md is readable

## Review Requirements

- Human reviews the report before acting on it
- Report is advisory, not authoritative

## Things Agents Must Never Do

- **Never close issues** — triage only
- **Never assign issues** — triage only
- **Never add or remove labels** — triage only
- **Never merge PRs** — triage only
- **Never modify source code** — this loop reads and reports

## Communication

- The report should be clear enough that a new team member can understand it
- Flag anything unusual (sudden spike in issues, PRs with 100+ files changed)
- If the GitHub API returns an error, report it in STATE.md and stop
