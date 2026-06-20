# Module 10: Capstone Project

> **Design and document a full L1 loop for a real repo of your choosing, using every template in this repo.**

---

## The Assignment

Design and document a loop engineering system for a real repository. This is not a coding exercise — it's a design exercise. You will produce documentation, not code.

**What you'll create:**
1. A completed design canvas
2. A skill file (SKILL.md)
3. A vision file (VISION.md)
4. An agent rules file (AGENTS.md)
5. A state file (STATE.md)
6. A pre-flight checklist
7. A retrospective

---

## Step 1: Choose a Repository

Pick a real repository you work on or care about. It can be:
- Your own project
- An open-source project you contribute to
- A project you maintain at work

Requirements:
- The repository must exist and be accessible to you
- It should have a git history (at least 10 commits)
- It should have at least one of: issues, pull requests, a test suite, dependencies

---

## Step 2: Complete the Design Canvas

Use [templates/first-loop-design-canvas.md](../../templates/first-loop-design-canvas.md). Fill in every field.

**Goal:** What should the loop accomplish? (One sentence.)

**Verification condition:** How do you know the loop succeeded? (Must be objectively checkable — not "looks good" but "a file exists with at least N entries.")

**Building blocks used:** Check all that apply. For L1, you need at minimum: automations, skills, memory/state.

**Cadence:** How often should the loop run?

**Starting maturity tier:** Default L1.

**Kill switch / spend cap:** How do you stop the loop? What's the maximum you'll spend?

**Owner:** Who reads the output?

---

## Step 3: Create the Skill File

Use [templates/SKILL.md.template](../../templates/SKILL.md.template). Write a real SKILL.md for the chosen repository.

It must include:
- Project conventions (language, framework, build tools)
- Build steps
- Things not to do (and why)
- Usage description

---

## Step 4: Create the Vision and Agent Rules

Use [templates/VISION.md.template](../../templates/VISION.md.template) and [templates/AGENTS.md.template](../../templates/AGENTS.md.template).

VISION.md should answer: what is this project building toward?

AGENTS.md should answer: what rules should agents follow in this repo?

---

## Step 5: Create the State File

Use [templates/STATE.md.template](../../templates/STATE.md.template). Initialize it with the current state (no runs yet, first run planned).

---

## Step 6: Complete the Pre-Flight Checklist

Use [templates/loop-design-checklist.md](../../templates/loop-design-checklist.md). Check off every item that's ready. Note every item that isn't.

---

## Step 7: Run the Loop (Optional but Recommended)

If you can, actually run the loop at L1 for at least 3 days. Record what happens in the STATE.md.

---

## Step 8: Write the Retrospective

After running the loop (or after designing it if you can't run it), write a 500-word retrospective answering:

1. **What worked?** Which parts of the design were effective?
2. **What didn't work?** Which parts needed adjustment?
3. **What would you change before considering L2?** What would need to be different to justify giving the loop more autonomy?
4. **What surprised you?** What did you learn that you didn't expect?

---

## Deliverable

A directory in your project (or a new directory) containing:

```
capstone/
├── design-canvas.md
├── skills/SKILL.md
├── VISION.md
├── AGENTS.md
├── STATE.md
├── pre-flight-checklist.md
└── retrospective.md
```

---

## Evaluation Rubric

| Criterion | Points |
|-----------|--------|
| Design canvas is complete and specific | 20 |
| SKILL.md is accurate for the chosen repo | 20 |
| VISION.md and AGENTS.md are relevant | 15 |
| STATE.md is properly initialized | 10 |
| Pre-flight checklist is honest (gaps identified) | 15 |
| Retrospective is thoughtful and specific | 20 |

---

## Try It Yourself

**Goal:** Complete the capstone project.

**Steps:**
1. Choose a repository.
2. Fill out every template.
3. Write the retrospective.
4. (Optional) Run the loop for 3 days.

**Success condition:** You have a `capstone/` directory with all 7 files, each containing real, specific content for a real repository. The retrospective identifies at least 2 things you'd change.

---

**Previous:** [Module 09 — Advanced Topics](../09-advanced-topics/README.md)
**Back to:** [README](../../README.md)
