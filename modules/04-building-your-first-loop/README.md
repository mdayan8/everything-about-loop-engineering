# Module 04: Building Your First Loop

> **A hands-on walkthrough: design, wire, and run a Changelog Drafter loop — the lowest-risk, lowest-cost pattern for your first loop.**

---

## Why the Changelog Drafter?

Your first loop should be:
- **Low risk** — it can't break anything
- **Low cost** — minimal token usage
- **Easy to verify** — you can immediately tell if it worked
- **Immediately useful** — the output has real value

The Changelog Drafter checks your git history, identifies meaningful changes, and writes a draft changelog. It reads, it writes a report, it changes nothing. It's an L1 loop — pure observation.

---

## Step 1: Fill Out the Design Canvas

Open [templates/first-loop-design-canvas.md](../../templates/first-loop-design-canvas.md) and fill it in. Here's what each field should look like for a Changelog Drafter:

### Goal (one sentence)
> Draft a changelog from recent git commits, categorizing them by type.

### Verification condition (must be objectively checkable)
> A file exists at `reports/changelog-draft.md` containing at least one section per commit type found in the git log.

### Building blocks used
- [x] Automations
- [ ] Worktrees
- [x] Skills
- [ ] Plugins & Connectors
- [ ] Sub-Agents
- [x] Memory & State

### Cadence
Daily (or on-demand for your first run)

### Starting maturity tier
L1 (report only — writes a draft, changes nothing)

### Kill switch / spend cap
- **Kill switch:** Remove the cron job or delete the workflow file
- **Spend cap:** None needed for L1 (report-only loops are minimal cost)

### Owner
You (who reads the output and decides what to do with it)

---

## Step 2: Create the Skill File

Create `skills/SKILL.md` at the project root:

```markdown
# Skill: Changelog Drafter

## Project Conventions
- This project uses Conventional Commits (feat:, fix:, docs:, chore:, etc.)
- The changelog follows Keep a Changelog format

## Build Steps
- No build required — this is a report-only loop

## Things Not to Do
- Do not modify source code
- Do not modify git history
- Do not create commits
- Do not merge any pull requests

## Usage
Drafts a changelog from recent git commits. Reads git log, categorizes 
commits by type, and writes a draft changelog to reports/changelog-draft.md.
```

---

## Step 3: Create the State File

Create `STATE.md` at the project root using [templates/STATE.md.template](../../templates/STATE.md.template):

```markdown
# Loop State: Changelog Drafter

## Tried
- (none yet — first run)

## Passed
- (none yet — first run)

## Still Open
- Run the initial changelog draft

## Last Run Timestamp
- Never (awaiting first run)

## Next Steps
1. Read git log for the last 30 days
2. Categorize commits by type
3. Write draft changelog to reports/changelog-draft.md
4. Update this STATE.md with results
```

---

## Step 4: Create the Prompt File

Create `prompts/changelog-drafter.md`:

```markdown
# Changelog Drafter Prompt

You are a changelog drafting agent. Your job is to read the recent git 
history and produce a draft changelog.

## Instructions

1. Read the git log for the last 30 days: `git log --oneline --since="30 days ago"`
2. Categorize each commit by type (feat, fix, docs, chore, refactor, test, perf, ci, build)
3. Group commits under appropriate changelog sections
4. Write the draft changelog to `reports/changelog-draft.md`
5. Update `STATE.md` with:
   - What you found (number of commits, categories)
   - What you wrote
   - When you ran

## Rules
- Do NOT modify any source code
- Do NOT create any commits
- Do NOT modify git history
- Only read from git and write to reports/ and STATE.md
- If no commits are found, write "No changes in the last 30 days" to the report
```

---

## Step 5: Create the Reports Directory

```bash
mkdir -p reports
```

---

## Step 6: Run the Loop

You have three options:

### Option A: Run Manually (Recommended for First Time)

```bash
# If using Claude Code:
claude --prompt-file prompts/changelog-drafter.md

# Or paste the prompt contents into your agent manually
```

### Option B: GitHub Actions

Create `.github/workflows/changelog-drafter.yml`:

```yaml
name: Changelog Drafter
on:
  schedule:
    - cron: '0 9 * * *'  # Daily at 9am UTC
  workflow_dispatch:

jobs:
  draft:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
        with:
          fetch-depth: 0  # Full git history needed
      - name: Draft changelog
        run: claude --prompt-file prompts/changelog-drafter.md
      - name: Upload draft
        uses: actions/upload-artifact@v4
        with:
          name: changelog-draft
          path: reports/changelog-draft.md
```

### Option C: Claude Code's Built-In Scheduling

If using Claude Code with native scheduling, configure the loop through the `/ralph-loop` command or equivalent.

---

## Step 7: Verify the Output

After the loop runs, check:

1. **Does `reports/changelog-draft.md` exist?**
2. **Does it contain categorized commits?**
3. **Does `STATE.md` reflect what the agent did?**
4. **Did the agent change anything it shouldn't have?** (git status should show no source code changes)

```bash
# Quick verification
ls reports/changelog-draft.md
cat STATE.md
git status  # Should show no code changes
```

---

## What Just Happened

You built and ran a loop with three components:
1. **Automation** (manual trigger or scheduled)
2. **Skill** (the SKILL.md that told the agent what to do and not do)
3. **Memory** (the STATE.md that persisted the result)

This is the minimum viable loop. Everything else in loop engineering builds on this pattern.

---

## What to Do Next

1. **Run it daily for a week.** See if the output is useful. Tweak the prompt if needed.
2. **Read the STATE.md after each run.** Does it accurately reflect what happened?
3. **Consider adding a sub-agent.** Have a second agent verify the changelog draft is accurate.
4. **Consider automating further.** Schedule it to run on its own.

But don't rush. Stay at L1. Get comfortable with the pattern before adding complexity.

---

## Try It Yourself

**Goal:** Build and run a Changelog Drafter loop from scratch.

**Steps:**
1. Fill out `templates/first-loop-design-canvas.md` for the Changelog Drafter pattern.
2. Create `skills/SKILL.md` with project conventions.
3. Create `STATE.md` with the template.
4. Create `prompts/changelog-drafter.md` with the prompt.
5. Run the loop (manually or via automation).
6. Verify the output exists and is correct.

**Success condition:** You have a `reports/changelog-draft.md` file with categorized commits from your repository, and a `STATE.md` that reflects the run. You did not modify any source code.

---

**Previous:** [Module 03 — The Five Building Blocks](../03-the-five-building-blocks/README.md)
**Next:** [Module 05 — The Maturity Model](../05-the-maturity-model/README.md)
