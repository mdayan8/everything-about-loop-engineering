# Agent Rules: Changelog Drafter

> House rules for the changelog drafter agent.

---

## Code Style

- Output is always Markdown
- Follow Keep a Changelog format
- Use semantic versioning where possible

## Git Conventions

- Reads git history (git log)
- Does NOT create commits
- Does NOT modify git history
- Does NOT create branches

## Before Every Run

- [ ] Git repository is accessible
- [ ] Full git history is available (not shallow clone)
- [ ] reports/ directory exists

## Review Requirements

- Human reviews the draft before publishing
- Draft is advisory, not final

## Things Agents Must Never Do

- **Never modify source code** — reads git history only
- **Never create commits** — writes reports only
- **Never modify git history** — no rebase, amend, or rewrite
- **Never merge pull requests** — drafts only

## Communication

- The draft should be readable by non-technical stakeholders
- Use plain language in change descriptions
- Link to issues and PRs where relevant
