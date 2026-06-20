# Project 01: Hello Loop

> Your first loop. Run it in 5 minutes. See the pattern in action.

---

## Goal

Run a loop that reads your git history and writes a commit activity report.

## What This Loop Does

1. Reads `git log` for the last 30 days
2. Counts commits per author
3. Identifies the most active files
4. Writes a report to `reports/hello-loop-report.md`
5. Updates `STATE.md`

## What This Loop Never Does

- Never modifies source code
- Never creates commits
- Never modifies git history

## Files

| File | Purpose |
|------|---------|
| `SKILL.md` | Agent conventions |
| `prompt.md` | The prompt the agent receives |
| `STATE.md` | Persistent memory |
| `config.yml` | GitHub Actions workflow |

---

## Step-by-Step Setup

### 1. Copy Files

```bash
cd /path/to/your-repo
cp -r /path/to/everything-about-loop-engineering/projects/project-01-hello-loop/* .
mkdir -p reports
```

### 2. Run the Loop

**Option A: Claude Code**
```bash
claude --prompt-file prompt.md
```

**Option B: Codex**
```bash
codex --prompt-file prompt.md --approval-mode full-auto
```

**Option C: GitHub Actions**
```bash
cp config.yml .github/workflows/hello-loop.yml
git add .github/workflows/hello-loop.yml
git commit -m "chore: add hello-loop automation"
git push
```

### 3. Check the Output

```bash
cat reports/hello-loop-report.md
```

You should see a report like:
```markdown
# Git Activity Report

Period: 2026-05-21 to 2026-06-20

## Commits by Author
| Author | Commits |
|--------|---------|
| mdayan | 42 |
| dependabot | 5 |

## Most Active Files
| File | Changes |
|------|---------|
| src/main.py | 12 |
| README.md | 8 |

## Summary
- Total commits: 47
- Active authors: 2
- Most active day: Tuesday
```

### 4. Check the State

```bash
cat STATE.md
```

The state file should now show:
```markdown
## Tried
- First run completed

## Passed
- Git log readable
- Report generated

## Still Open
- (none)

## Last Run Timestamp
- 2026-06-20T...
```

---

## Success Criteria

- [ ] `reports/hello-loop-report.md` exists
- [ ] Report contains commit counts by author
- [ ] Report contains most active files
- [ ] `STATE.md` is updated with timestamp
- [ ] No source code was modified

---

## What to Do Next

1. **Run it daily** — watch the report change over time
2. **Add a sub-agent** — verify the report is accurate
3. **Increase to L2** — have the loop suggest commit message improvements
4. **Build Project 02** — add dependency checking

---

## Troubleshooting

| Problem | Solution |
|---------|----------|
| "git: command not found" | Install git: `brew install git` |
| "No commits in the last 30 days" | The repo is inactive — try a different repo |
| Report is empty | Check that the repo has git history |
