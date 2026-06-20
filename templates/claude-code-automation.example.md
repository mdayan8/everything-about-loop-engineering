# Claude Code Automation Examples

> **These are illustrative examples to adapt, not copy-paste production configurations.** Exact syntax and flags depend on your Claude Code version.

---

## Example 1: Scheduled Changelog Drafter (Daily)

A loop that runs once daily, reads git history, and writes a draft changelog.

### GitHub Actions Workflow

```yaml
# .github/workflows/changelog-drafter.yml
name: Changelog Drafter
on:
  schedule:
    - cron: '0 9 * * *'  # 9am UTC daily
  workflow_dispatch:

jobs:
  draft:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
        with:
          fetch-depth: 0  # Full history needed

      - name: Run changelog drafter
        run: |
          claude \
            --prompt-file prompts/changelog-drafter.md \
            --state-file STATE.md \
            --max-turns 5

      - name: Upload draft
        uses: actions/upload-artifact@v4
        with:
          name: changelog-draft-${{ github.run_id }}
          path: reports/changelog-draft.md

      - name: Commit state changes
        run: |
          git config user.name "changelog-drafter-bot"
          git config user.email "bot@example.com"
          git add STATE.md
          git diff --staged --quiet || git commit -m "chore: update loop state"
          git push
```

### Prompt File (prompts/changelog-drafter.md)

```markdown
You are a changelog drafting agent. Read the git log for the last 30 days 
and produce a draft changelog.

1. Run: git log --oneline --since="30 days ago"
2. Categorize commits by type (feat, fix, docs, chore, refactor, test, perf, ci)
3. Group commits under appropriate changelog sections
4. Write the draft to reports/changelog-drafter.md
5. Update STATE.md with what you found and what you wrote

Rules: Do NOT modify source code. Do NOT create commits. 
Only read from git and write to reports/ and STATE.md.
```

---

## Example 2: Goal-Condition Verification Run

A separate, smaller model verifies that a condition is true after each agent turn.

### Configuration

```toml
# .claude/verify.toml
[verification]
enabled = true
model = "claude-haiku"  # Smaller, faster model for verification
prompt = """
You are a verification agent. Your ONLY job is to check whether 
a condition is true. Do not make changes. Do not suggest improvements.

Condition: {{condition}}

Read the specified files and determine whether the condition is met.
Respond with exactly: PASS or FAIL, followed by a one-sentence explanation.
"""
max_retries = 3
```

### Usage in a Loop

The acting agent makes a change. The verifier checks:

```
Maker:  "I updated the test file to cover the new function."
Verifier: "PASS — test file contains a test for the new function 
          and the test passes."
```

---

## Example 3: Worktree-Isolated Sub-Agent

A sub-agent runs in its own worktree to avoid collisions with the main agent.

### Claude Code Configuration

```toml
# .claude/subagents/dependency-updater.toml
name = "dependency-updater"
description = "Checks for outdated dependencies and proposes updates"
model = "claude-sonnet"
worktree = true  # Isolate in its own worktree
branch_prefix = "loop/dep-update"

instructions = """
You are a dependency update agent. Your job is to:
1. Check for outdated dependencies
2. Propose updates with changelogs
3. Run tests to verify the update doesn't break anything
4. Write a summary to reports/dependency-updates.md

Rules:
- Only propose patch-level updates (1.2.3 → 1.2.4)
- Do NOT propose major version updates
- Run the full test suite after each update
- If tests fail, revert and report the failure
- Update STATE.md with your findings
"""
```

---

## Example 4: Full Loop with Sub-Agent Verification

A complete loop with a maker agent, a checker agent, and state persistence.

### Loop Definition

```toml
# .claude/loop/pr-reviewer.toml
name = "pr-reviewer"
description = "Reviews open PRs for code quality and test coverage"

[maker]
model = "claude-sonnet"
prompt_file = "prompts/review-pr.md"
worktree = false  # Read-only, no worktree needed

[checker]
model = "claude-haiku"
prompt = """
You are a verification agent. The maker agent has reviewed a PR.
Your job is to verify:
1. Does the review reference actual file changes? (Not generic feedback)
2. Are the test coverage claims accurate? (Check the test files)
3. Are the security concerns specific? (Not vague warnings)

Respond with: VERIFIED or NEEDS_REVISION, followed by specific findings.
"""
worktree = false

[state]
file = "STATE.md"
update_after_each_run = true

[schedule]
cron = "*/15 * * * *"  # Every 15 minutes
max_concurrent = 1
```

---

## Adapting These Examples

1. **Start simple.** Example 1 (Changelog Drafter) is the best starting point.
2. **Add complexity gradually.** Add verification (Example 2) only after the basic loop works.
3. **Add worktrees (Example 3) only when you have multiple loops.**
4. **Full loop with sub-agents (Example 4) is the most complex.** Only use when L1 is proven.

These examples are starting points. Your actual configuration will depend on your agent tool, your project, and your specific needs.
