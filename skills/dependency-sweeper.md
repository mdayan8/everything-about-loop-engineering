# Skill: Dependency Sweeper

> **Usage:** Checks for outdated dependencies and proposes updates with changelogs and compatibility notes.

---

## Project Conventions

- **Type:** Advisory loop (L2) — proposes changes, human merges
- **Output:** PR with dependency updates + report in `reports/dependency-updates.md`
- **Frequency:** Every 6 hours to once daily
- **Token cost:** Medium (~$0.20–$0.80/run)

## What This Loop Does

1. Checks for outdated dependencies
2. Categorizes updates: patch, minor, major
3. For patch updates: runs update, runs tests, commits if tests pass
4. For minor updates: writes proposal, does not commit
5. For major updates: flags for human review
6. Writes summary report
7. Updates STATE.md

## What This Loop Must Never Do

- **Never propose major version updates** — flag for human
- **Never skip tests** — always verify after update
- **Never commit if tests fail** — revert and report
- **Never update production databases** — code dependencies only

## Update Rules

| Update Type | Action | Commit? |
|-------------|--------|---------|
| Patch (1.2.3 → 1.2.4) | Auto-update, run tests | Yes, if tests pass |
| Minor (1.2.x → 1.3.0) | Write proposal | No |
| Major (1.x → 2.0) | Flag for human | No |

## Prompt Template

```markdown
You are a dependency update agent. Check for outdated dependencies 
and propose updates.

## Instructions

1. Run the outdated check for this project:
   - npm: npm outdated
   - pip: pip list --outdated
   - go: go list -m -u all
2. For each outdated dependency:
   - Classify: patch / minor / major
   - Check changelog for breaking changes
   - Check compatibility with current framework version
3. For patch updates:
   - Run the update
   - Run the test suite
   - If tests pass, commit the change
   - If tests fail, revert and report the failure
4. For minor updates:
   - Write proposal to reports/dependency-updates.md
   - Do NOT commit
5. For major updates:
   - Flag in report as "requires human review"
   - Do NOT commit
6. Update STATE.md

## Rules
- Only auto-commit patch-level updates
- Always run tests before committing
- If tests fail, revert and report
- Never update major versions without human approval
```

## Verification Condition

For patch updates: tests pass after the update.
For all updates: `reports/dependency-updates.md` exists with categorized findings.

## Safety Notes

- Start with a single project to validate the loop
- Monitor the first few runs closely
- Set a daily token cap
- Consider using a lock file to prevent unexpected updates
