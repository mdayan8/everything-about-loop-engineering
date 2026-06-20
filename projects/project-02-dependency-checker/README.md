# Project 02: Dependency Checker

> Build a loop that catches outdated dependencies before they become vulnerabilities.

---

## Goal

Run a loop that checks for outdated dependencies and proposes safe updates.

## What This Loop Does

1. Checks for outdated npm/pip/go dependencies
2. Categorizes: patch (safe), minor (caution), major (flag for human)
3. For patch updates: proposes the update with changelog
4. Writes a report to `reports/dependency-report.md`
5. Updates `STATE.md`

## What This Loop Never Does

- Never commits code
- Never updates major versions without human approval
- Never skips test verification

## Setup

```bash
cd /path/to/your-repo
cp -r /path/to/everything-about-loop-engineering/projects/project-02-dependency-checker/* .
mkdir -p reports
```

## Run

```bash
claude --prompt-file prompt.md
```

## Success Criteria

- [ ] `reports/dependency-report.md` exists
- [ ] Report categorizes updates by type (patch/minor/major)
- [ ] Patch updates include proposed commands
- [ ] `STATE.md` is updated
- [ ] No code was modified
