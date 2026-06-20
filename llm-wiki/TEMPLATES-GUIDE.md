# LLM Wiki: Templates Guide

> How to use every template in this repository. Each template is fill-in-the-blank — replace placeholder text with your specific content.

---

## Template Overview

| Template | When to Use | Required Fields |
|----------|-------------|-----------------|
| [SKILL.md.template](../templates/SKILL.md.template) | Every project | Language, framework, build steps, things not to do |
| [VISION.md.template](../templates/VISION.md.template) | Every project | Goal, current state, priorities |
| [AGENTS.md.template](../templates/AGENTS.md.template) | Every project | Code style, git conventions, things agents must never do |
| [STATE.md.template](../templates/STATE.md.template) | Every loop | Tried, passed, still open, last run timestamp |
| [First Loop Design Canvas](../templates/first-loop-design-canvas.md) | First loop only | Goal, verification condition, building blocks, cadence, tier, kill switch, owner |
| [Loop Design Checklist](../templates/loop-design-checklist.md) | Before L2+ | All items checked or gaps identified |
| [Claude Code Examples](../templates/claude-code-automation.example.md) | Claude Code users | Adapt examples to your use case |
| [Codex Examples](../templates/codex-automation.example.md) | Codex users | Adapt examples to your use case |
| [Sub-Agent Definition](../templates/subagent-definition.toml.template) | Sub-agent loops | Maker config, checker config, schedule |

---

## SKILL.md.template

**Purpose:** Tells the agent the rules of your project.

**Fill in:**
1. **Usage description** — One tight, boring sentence. "Builds and tests the API server for the payments service." Beats a clever description for agent matching.
2. **Project conventions** — Language, framework, package manager, test framework, linting, formatting.
3. **Build steps** — Exact commands for install, build, test, lint, format.
4. **Things not to do** — And why. "Do not modify migration files without running the full test suite."
5. **Environment variables** — What the agent needs to know about.

**Example (completed):**
```markdown
# Skill: Payments API

> **Usage:** Builds and tests the API server for the payments service.

## Project Conventions
- **Language:** TypeScript
- **Framework:** Express.js
- **Package Manager:** npm
- **Test Framework:** Jest
- **Linting:** ESLint
- **Formatting:** Prettier

## Build Steps
npm install
npm run build
npm test
npm run lint

## Things Not to Do
- Do not modify database migrations without running the full test suite
- Do not skip type checking
- Do not commit .env files
```

---

## VISION.md.template

**Purpose:** Anchors what agents should be building toward.

**Fill in:**
1. **Goal** — One paragraph: what does success look like?
2. **Current state** — Where is the project now?
3. **Priorities** — Top 3 things to work on next.
4. **Non-goals** — What this project explicitly does NOT do.

---

## AGENTS.md.template

**Purpose:** House rules for agent behavior.

**Fill in:**
1. **Code style** — Indentation, line length, file maximum.
2. **Git conventions** — Commit format, branch naming, PR requirements.
3. **Before every commit** — Tests pass? Linter passes? No secrets?
4. **Things agents must never do** — Hardcode secrets? Skip tests? Override humans?

---

## STATE.md.template

**Purpose:** Persistent memory across agent runs.

**Fill in (initially):**
```markdown
## Tried
- (none yet — first run)

## Passed
- (none yet — first run)

## Still Open
- [ ] [First task]

## Last Run Timestamp
- Never (awaiting first run)
```

**Update after each run:**
- Move completed items from "Still Open" to "Passed"
- Add new findings to "Tried"
- Add new tasks to "Still Open"
- Update timestamp

---

## First Loop Design Canvas

**Purpose:** One-page worksheet for planning your first loop.

**Every field is required:**

1. **Goal** — One sentence. "Draft a changelog from recent git commits."
2. **Verification condition** — Objectively checkable. "A file exists at reports/changelog-draft.md containing at least one section per commit type."
3. **Building blocks** — Check all that apply (minimum: automations + memory/state).
4. **Cadence** — How often. "Daily" or "Every 6 hours."
5. **Starting maturity tier** — Default L1.
6. **Kill switch** — How to stop. "Remove the cron job."
7. **Spend cap** — Maximum budget. "None needed for L1."
8. **Owner** — Who reads output. "Me."

---

## Loop Design Checklist

**Purpose:** Pre-flight check before enabling L2+ loops.

**Use this before every L2+ loop launch:**
1. Print or open the checklist
2. Check off every ready item
3. Note every gap
4. Fix gaps before launching
5. Sign off with date and name

**Items that are always required (even for L1):**
- Verifier sub-agent or objective success criteria
- Spend cap
- Kill switch tested
- Scope narrow enough for current tier
- Human review point defined

---

*See [../templates/](../templates/) for the actual template files. See [PATTERNS.md](PATTERNS.md) for how templates are used in production patterns.*
