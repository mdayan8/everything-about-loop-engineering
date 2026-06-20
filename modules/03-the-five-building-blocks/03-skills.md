# Skills

> **A folder holding written-down project conventions, so the agent doesn't re-derive project context from zero every run.**

---

## Plain English

Every project has unwritten rules: the build command, the test framework, the coding style, the things that will break if you touch them. When you work on a project long enough, you internalize these rules. An agent doesn't.

A skill is a file (conventionally `SKILL.md`) that writes those rules down. Instead of the agent spending tokens figuring out "what framework does this project use?" every time, it reads the skill file and knows immediately.

Think of it like a new employee onboarding document — but for an AI.

---

## Technical Detail

### The Skill File

A skill file typically lives in a `skills/` directory and contains:

1. **Project conventions** — framework, language, build tools, test framework
2. **Build steps** — how to install dependencies, run tests, build the project
3. **Things not to do** — and why (e.g., "don't modify the migration files without running the full test suite")
4. **Usage description** — a tight, boring description that helps the agent match the right skill to the right task

See [templates/SKILL.md.template](../../templates/SKILL.md.template) for a fill-in-the-blank version.

### Supporting Files

Skills are often paired with two other files:

- **`VISION.md`** — what the project is building toward. Anchors the agent's work on the right goal.
- **`AGENTS.md`** — house rules for agent behavior. What the agent should never do, how code should be reviewed, what conventions to follow.

See [templates/VISION.md.template](../../templates/VISION.md.template) and [templates/AGENTS.md.template](../../templates/AGENTS.md.template).

### Why This Matters for Loops

A loop runs repeatedly. Without a skill file, every run starts by asking the agent to figure out the project context — wasting tokens and producing inconsistent results. With a skill file, every run starts with the same foundation.

```
Without skill:  Agent reads project → guesses framework → guesses build command → maybe gets it right
With skill:     Agent reads SKILL.md → knows framework → knows build command → starts working immediately
```

---

## How It Fails If Skipped

Without skills, each loop run:
- Wastes tokens re-deriving project context
- May make inconsistent decisions (different runs choose different approaches)
- May break things the agent didn't know were fragile
- Takes longer because it has to discover everything from scratch

---

## Try It Yourself

**Goal:** Create a minimal skill file for a project you work on.

**Steps:**
1. Pick a project directory you're familiar with.
2. Answer these questions (you don't need to write the file yet — just answer):
   - What language/framework is this project?
   - What's the build command?
   - What's the test command?
   - What should the agent never touch?
3. Write a `SKILL.md` file (use [templates/SKILL.md.template](../../templates/SKILL.md.template) as a guide).
4. Place it in a `skills/` directory at the project root.

**Success condition:** You have a `skills/SKILL.md` file that answers at least three of the four questions above. An agent reading this file would know the project basics without exploring the codebase.

---

**Previous:** [Worktrees](02-worktrees.md)
**Next:** [Plugins & Connectors](04-plugins-and-connectors.md)
