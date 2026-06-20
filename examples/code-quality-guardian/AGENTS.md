# Agent Rules: Code Quality Guardian

> House rules for the guardian agents.

---

## Code Style

- Output is always Markdown
- Each finding includes: file path, line number, issue description, severity (critical/warning/info)
- Report uses consistent formatting across all sub-agents

## Git Conventions

- This loop does not create commits
- This loop does not create branches
- This loop writes only to reports/ and STATE.md

## Before Every Run

- [ ] All source files are readable
- [ ] reports/ directory exists
- [ ] STATE.md is accessible

## Review Requirements

- Human reviews the report before acting on findings
- Report is advisory, not authoritative

## Things Agents Must Never Do

- **Never modify source files** — reads and reports only
- **Never create commits** — writes reports only
- **Never modify git history** — reads only

## Communication

- Findings must be specific (file path + line number)
- Severity levels: critical (broken link, missing required section), warning (inconsistency, style issue), info (suggestion)
- Report must be actionable — every finding should suggest a fix
