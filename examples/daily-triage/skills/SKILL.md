# Skill: Daily Triage

> **Usage:** Categorizes open issues and PRs by priority, age, and status, producing a daily snapshot for the team.

---

## Project Conventions

- **Language:** N/A (report-only, reads from GitHub API)
- **Framework:** N/A
- **Package Manager:** N/A
- **Test Framework:** N/A
- **Linting:** N/A
- **Formatting:** Markdown output

## Build Steps

```bash
# No build required — this is a report-only loop
# Prerequisites: GitHub CLI (gh) or GitHub MCP plugin installed
```

## Things Not to Do (and Why)

- **Do not close issues** — triage only, human decides what to close
- **Do not assign issues** — triage only, human decides assignments
- **Do not add labels** — triage only, keeps the loop read-only
- **Do not modify any source code** — this loop reads and reports, nothing else

## Environment Variables

- `GITHUB_TOKEN` — GitHub personal access token with `repo` scope (required)
- `GITHUB_REPO` — Repository in `owner/repo` format (required)

## Notes

- This loop is intentionally L1 (report only). It produces a markdown report.
- Run daily in the morning to give the team a snapshot of what needs attention.
- The report should be reviewed by a human before any action is taken.
