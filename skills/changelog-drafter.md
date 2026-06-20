# Skill: Changelog Drafter

> **Usage:** Drafts a changelog from recent git commits, categorizing them by type using Conventional Commits.

---

## Project Conventions

- **Type:** Report-only loop (L1)
- **Output:** Markdown changelog in `reports/changelog-draft.md`
- **Frequency:** Daily or per-release
- **Token cost:** Low (~$0.05–$0.15/run)

## What This Loop Does

1. Reads git log for the last 30 days (or since last release)
2. Categorizes commits by type: feat, fix, docs, chore, refactor, test, perf, ci, build
3. Groups commits under appropriate changelog sections
4. Highlights breaking changes
5. Writes draft changelog
6. Updates STATE.md

## What This Loop Must Never Do

- **Never modify source code** — reads git history only
- **Never create commits** — writes reports only
- **Never modify git history** — no rebase, amend, or rewrite
- **Never merge pull requests** — drafts only

## Commit Category Reference

| Prefix | Category | Example |
|--------|----------|---------|
| `feat:` | New feature | `feat: add user authentication` |
| `fix:` | Bug fix | `fix: resolve null pointer in UserService` |
| `docs:` | Documentation | `docs: update API reference` |
| `chore:` | Maintenance | `chore: update dependencies` |
| `refactor:` | Code restructuring | `refactor: extract validation logic` |
| `test:` | Tests | `test: add integration tests for auth` |
| `perf:` | Performance | `perf: optimize database queries` |
| `ci:` | CI/CD | `ci: add GitHub Actions workflow` |
| `build:` | Build system | `build: migrate to Vite` |

## Prompt Template

```markdown
You are a changelog drafting agent. Read the git log and produce 
a draft changelog.

## Instructions

1. Run: git log --oneline --since="30 days ago"
2. Categorize each commit by type (feat, fix, docs, chore, etc.)
3. Group commits under appropriate changelog sections
4. Flag any breaking changes (commits with "BREAKING" or "!" in scope)
5. Write draft to reports/changelog-draft.md
6. Update STATE.md with: timestamp, commit count, categories found

## Rules
- Do NOT modify source code
- Do NOT create commits
- Do NOT modify git history
- Only read from git and write to reports/ and STATE.md
- If no commits found, write "No changes in the last 30 days"
```

## Verification Condition

A file exists at `reports/changelog-draft.md` containing:
- At least one section per commit type found
- Commit messages listed under appropriate sections
- Date range specified

## Success Checklist

- [ ] `reports/changelog-draft.md` exists
- [ ] Changelog is categorized by commit type
- [ ] At least one section per commit type present
- [ ] `STATE.md` is updated with run timestamp
- [ ] No source code was modified
- [ ] No commits were created or modified
