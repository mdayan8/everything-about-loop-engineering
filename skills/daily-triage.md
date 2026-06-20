# Skill: Daily Triage

> **Usage:** Categorizes open issues and PRs by priority, age, and status, producing a daily snapshot for the team.

---

## Project Conventions

- **Type:** Report-only loop (L1)
- **Output:** Markdown report in `reports/triage.md`
- **Frequency:** Once daily (morning recommended)
- **Token cost:** Low (~$0.05–$0.20/run)

## What This Loop Does

1. Reads all open issues in the repository
2. Reads all open pull requests
3. Categorizes by priority: urgent, normal, low
4. Flags stale items (7+ days with no activity)
5. Writes a summary report
6. Updates STATE.md

## What This Loop Must Never Do

- **Never close issues** — triage only
- **Never assign issues to people** — triage only
- **Never add or remove labels** — triage only
- **Never merge pull requests** — triage only
- **Never modify source code** — reads and reports only

## Prompt Template

```markdown
You are a daily triage agent. Your job is to produce a snapshot of 
what needs attention in this repository.

## Instructions

1. List all open issues with: title, age, labels, last activity date
2. List all open PRs with: title, age, CI status, review status
3. Categorize each item: urgent (needs action today), normal, low
4. Flag stale items: no activity in 7+ days
5. Write summary to reports/triage.md
6. Update STATE.md with: timestamp, items found, items flagged

## Rules
- Do NOT close, assign, or label anything
- Do NOT modify source code
- Do NOT merge PRs
- Only read from GitHub and write to reports/ and STATE.md
```

## Verification Condition

A file exists at `reports/triage.md` containing:
- Count of open issues
- Count of open PRs
- At least one categorized section (urgent/normal/low)
- Timestamp of when the report was generated

## Success Checklist

- [ ] `reports/triage.md` exists
- [ ] Report contains issue count and PR count
- [ ] Items are categorized by priority
- [ ] Stale items are flagged
- [ ] `STATE.md` is updated with run timestamp
- [ ] No source code was modified
- [ ] No issues were closed or assigned
