# Skill: Changelog Drafter

> **Usage:** Drafts a changelog from recent git commits, categorizing them by type using Conventional Commits.

---

## Project Conventions

- **Language:** N/A (reads git history, writes markdown)
- **Framework:** N/A
- **Package Manager:** N/A
- **Test Framework:** N/A
- **Linting:** N/A
- **Formatting:** Markdown, Keep a Changelog format

## Build Steps

```bash
# No build required — this is a report-only loop
# Prerequisites: git with full history (fetch-depth: 0)
```

## Things Not to Do (and Why)

- **Do not modify source code** — this loop reads git history, nothing else
- **Do not create commits** — this loop writes reports only
- **Do not modify git history** — never rebase, amend, or rewrite commits
- **Do not merge pull requests** — this loop drafts, human decides

## Notes

- This loop follows Conventional Commits (feat:, fix:, docs:, chore:, etc.)
- The changelog follows Keep a Changelog format
- This is the recommended first loop — lowest risk, lowest cost
- See Module 04 for the full walkthrough
