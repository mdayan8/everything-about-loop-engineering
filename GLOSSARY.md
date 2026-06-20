# Glossary

Alphabetized definitions of terms used throughout this repository.

---

## A

**Agent**
An AI system that can take actions (editing files, running commands, making API calls) rather than only generating text. A coding agent operates in a development environment with access to your filesystem, terminal, and tools. Contrast with a chatbot, which only generates text in response to prompts.

**Automation**
A scheduled or triggered run that turns a single agent session into an ongoing loop. May be implemented as a cron job, a GitHub Action, a lifecycle hook, or a built-in scheduling feature of a coding agent tool.

**AGENTS.md**
A project-level markdown file that defines house rules for how agents should behave within a repository. Conventionally placed at the repo root. Covers conventions, forbidden actions, coding style, and review requirements.

---

## B

**Building Block**
One of the six core components that make up a loop engineering system: automations, worktrees, skills, plugins & connectors, sub-agents, and memory/state. See [Module 03](modules/03-the-five-building-blocks/README.md).

---

## C

**CADENCE**
How frequently a loop runs. Examples: once daily, every 5–15 minutes, every 6 hours. Cadence is a key decision in loop design — too frequent wastes tokens, too infrequent misses timely issues.

**Claude Code**
Anthropic's AI coding agent, which operates in the terminal and has access to the filesystem, shell, and tools. Supports features like `/ralph-loop`, worktrees, and sub-agents. One of the two most-used coding agent products as of mid-2026.

**Control Loop**
A system that continuously monitors a condition and takes action to maintain it. Thermostats, Kubernetes controllers, and CI retry systems are all control loops. Loop engineering applies this pattern to AI coding agents. The shape is decades old; the integration with coding agents is new.

---

## D

**Design Canvas**
A structured worksheet used to plan a loop before building it. Captures goal, verification conditions, building blocks, cadence, maturity tier, kill switch, and owner. See [templates/first-loop-design-canvas.md](templates/first-loop-design-canvas.md).

---

## G

**Goal-Condition Primitive**
An in-session check where a separate, smaller model verifies whether a stated condition is actually true after each agent turn. This prevents the acting model from grading its own work. A key safety mechanism in automated loops.

---

## H

**HONESTY.md**
A project-level file that documents the limitations, claim classification, and disclaimers for a repository. Used in this project to maintain transparency about the field's age and the repo's scope. See [HONESTY.md](HONESTY.md).

---

## K

**Kill Switch**
A mechanism to immediately stop a running loop. Essential for any loop beyond L1. May be a file-based flag (e.g., a `STOP` file that the loop checks), an environment variable, or a process signal. Must be tested before enabling any unattended loop.

---

## L

**L1 (Report Only)**
The lowest maturity tier. The loop runs, finds things, writes them down, and changes nothing. Most loops should stay at L1 far longer than feels necessary.

**L2 (Assisted / Patch-Only)**
The middle maturity tier. The loop proposes narrow-scope changes (dependency bumps, lint fixes, changelog drafts). A human still reviews and merges.

**L3 (Unattended)**
The highest maturity tier. The loop commits, merges, or deploys on its own, inside guardrails already proven at L1/L2. Few tasks ever earn L3.

---

## M

**Maker/Checker**
A pattern where one agent (the maker) produces work and a second, independent agent (the checker) verifies it. Splitting these roles prevents the same model from grading its own work. Often implemented as sub-agents.

**Memory/State**
A durable file outside any single conversation that persists information across agent runs. The model itself forgets everything between sessions, so external state is essential for loops. Typically a markdown file (STATE.md) or a project board.

---

## P

**Plugin**
An extension built on MCP (Model Context Protocol) that lets an agent reach real tools — issue trackers, databases, chat systems, deployment platforms — instead of only the filesystem.

**Prompt**
A text instruction given to an AI model. In coding agents, prompts can include task descriptions, context files, error messages, and feedback from previous iterations.

**PR Babysitter**
A production pattern where a loop monitors pull requests every 5–15 minutes, checking for review readiness, CI status, and merge conflicts. Starts at L1 (watch only).

---

## R

**Ralph Loop**
The original technique for loop engineering, published by Geoffrey Huntley in July 2025. Wraps a coding agent in a bash `while true` loop, pipes in a prompt file, and lets it run unattended with state persisted to disk between runs. Named after the Ralph Wiggum blog post.

---

## S

**SKILL.md**
A markdown file that documents project conventions, build steps, coding style, and things not to do — so that an agent doesn't have to re-derive project context from scratch on every run. Conventionally placed in a `skills/` directory.

**Sub-Agent**
A second, independent agent that runs alongside or after the primary agent. May use a different model. Typically used for verification (maker/checker pattern) or for parallelizing independent tasks.

---

## T

**TDD (Test-Driven Development)**
A development practice where you write tests before writing implementation. In loop engineering, TDD provides a natural verification mechanism: a loop can run tests to check its own output.

---

## V

**VISION.md**
A project-level markdown file that describes what agents should be building toward — the long-term goal or direction of the project. Helps align multiple agent runs on the same objective.

---

## W

**Worktree**
An isolated working directory on its own git branch, sharing repo history. Prevents parallel agents from colliding on the same files. Supported natively in both Claude Code and Codex.
