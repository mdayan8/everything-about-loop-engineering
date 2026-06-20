# Codex Automation Examples

> **These are illustrative examples to adapt, not copy-paste production configurations.** Exact syntax depends on your Codex version.

---

## Example 1: Scheduled Changelog Drafter

A loop that runs once daily and drafts a changelog from git history.

### GitHub Actions Workflow

```yaml
# .github/workflows/codex-changelog.yml
name: Codex Changelog Drafter
on:
  schedule:
    - cron: '0 9 * * *'
  workflow_dispatch:

jobs:
  draft:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
        with:
          fetch-depth: 0

      - name: Set up Codex
        run: npm install -g @openai/codex

      - name: Run changelog drafter
        run: |
          codex \
            --prompt-file prompts/changelog-drafter.md \
            --state-file STATE.md \
            --approval-mode full-auto \
            --max-turns 5
        env:
          OPENAI_API_KEY: ${{ secrets.OPENAI_API_KEY }}

      - name: Upload draft
        uses: actions/upload-artifact@v4
        with:
          name: changelog-draft-${{ github.run_id }}
          path: reports/changelog-draft.md

      - name: Commit state
        run: |
          git config user.name "changelog-drafter-bot"
          git config user.email "bot@example.com"
          git add STATE.md
          git diff --staged --quiet || git commit -m "chore: update loop state"
          git push
```

---

## Example 2: Dependency Sweeper (L2 — Proposes, Human Merges)

A loop that checks for outdated dependencies and opens PRs with updates.

### GitHub Actions Workflow

```yaml
# .github/workflows/codex-deps.yml
name: Codex Dependency Sweeper
on:
  schedule:
    - cron: '0 */6 * * *'  # Every 6 hours
  workflow_dispatch:

jobs:
  sweep:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Set up Codex
        run: npm install -g @openai/codex

      - name: Check dependencies
        run: |
          codex \
            --prompt-file prompts/dependency-check.md \
            --state-file STATE.md \
            --approval-mode suggest \
            --max-turns 10
        env:
          OPENAI_API_KEY: ${{ secrets.OPENAI_API_KEY }}

      - name: Create PR if updates found
        if: hashFiles('reports/dependency-updates.md') != ''
        uses: peter-evans/create-pull-request@v6
        with:
          commit-message: "chore: dependency updates from automated sweep"
          title: "chore: automated dependency updates"
          body-file: reports/dependency-updates.md
          branch: automated/dependency-updates
```

### Prompt File (prompts/dependency-check.md)

```markdown
You are a dependency update agent. Check for outdated dependencies 
and propose updates.

1. Run the appropriate outdated dependency check for this project
   (npm outdated, pip list --outdated, go list -m -u all, etc.)
2. For each outdated dependency, check:
   - Is this a patch update? (safe to propose)
   - Is this a minor update? (propose with caution)
   - Is this a major update? (skip, flag for human)
3. Write proposed updates to reports/dependency-updates.md
4. For patch updates, run the update and run tests
5. If tests pass, commit the change
6. Update STATE.md

Rules:
- Only auto-commit patch-level updates
- Minor updates: write the proposal, don't commit
- Major updates: flag for human review
- Always run tests before committing
- If tests fail, revert and report the failure
```

---

## Example 3: PR Review Loop (L1 — Watch Only)

A loop that monitors PRs and writes a status report.

### GitHub Actions Workflow

```yaml
# .github/workflows/codex-pr-monitor.yml
name: Codex PR Monitor
on:
  schedule:
    - cron: '*/15 * * * *'  # Every 15 minutes
  workflow_dispatch:

jobs:
  monitor:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Set up Codex
        run: npm install -g @openai/codex

      - name: Monitor PRs
        run: |
          codex \
            --prompt-file prompts/pr-monitor.md \
            --state-file STATE.md \
            --approval-mode full-auto \
            --max-turns 3
        env:
          OPENAI_API_KEY: ${{ secrets.OPENAI_API_KEY }}
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

### Prompt File (prompts/pr-monitor.md)

```markdown
You are a PR monitoring agent. Your job is to check the status of 
open pull requests and report findings.

1. List all open PRs in this repository
2. For each PR, check:
   - CI status (are all checks passing?)
   - Review status (are required reviews approved?)
   - Merge conflicts (are there any?)
   - Age (how many days has it been open?)
3. Write a status report to reports/pr-status.md
4. Flag any PRs that need attention (failing CI, missing reviews, 
   merge conflicts, stale for > 7 days)
5. Update STATE.md

Rules: Do NOT modify any code. Do NOT merge any PRs. 
Only read from GitHub and write to reports/ and STATE.md.
```

---

## Adapting These Examples

1. **Start with Example 3 (PR Monitor, L1).** Lowest risk, immediate value.
2. **Add Example 1 (Changelog Drafter)** for another L1 pattern.
3. **Move to Example 2 (Dependency Sweeper, L2)** only after L1 patterns are proven.
4. **Adjust approval mode:** `full-auto` for L1 (no human approval needed), `suggest` for L2 (suggests changes, human approves), `auto` for L3 (applies changes directly).

These examples are starting points. Your actual configuration depends on your project and agent tool version.
