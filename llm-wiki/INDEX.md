# LLM Wiki: Master Index

> Every concept in loop engineering, mapped to its definition. Read this first.

---

## Core Concepts

| Concept | Definition | File |
|---------|-----------|------|
| **Loop Engineering** | The practice of designing the system that prompts an AI coding agent, rather than typing each prompt yourself | [CONCEPTS.md](CONCEPTS.md#loop-engineering) |
| **Coding Agent** | An AI system that can take actions (editing files, running commands) rather than only generating text | [CONCEPTS.md](CONCEPTS.md#coding-agent) |
| **Prompt** | A text instruction given to an AI model | [CONCEPTS.md](CONCEPTS.md#prompt) |
| **Prompt Engineering** | The practice of writing effective prompts for AI models | [CONCEPTS.md](CONCEPTS.md#prompt-engineering) |
| **Control Loop** | A system that continuously monitors a condition and takes action to maintain it | [CONCEPTS.md](CONCEPTS.md#control-loop) |
| **Ralph Loop** | The original loop technique: a bash `while true` loop piping a prompt file to a coding agent | [CONCEPTS.md](CONCEPTS.md#ralph-loop) |

## Building Blocks

| Block | Definition | File |
|-------|-----------|------|
| **Automations** | Scheduled or triggered runs that turn a single agent session into an ongoing loop | [CONCEPTS.md](CONCEPTS.md#automations) |
| **Worktrees** | Isolated working directories on their own branch, sharing repo history | [CONCEPTS.md](CONCEPTS.md#worktrees) |
| **Skills** | A folder holding written-down project conventions for agents | [CONCEPTS.md](CONCEPTS.md#skills) |
| **Plugins & Connectors** | Extensions built on MCP that let agents reach real tools | [CONCEPTS.md](CONCEPTS.md#plugins--connectors) |
| **Sub-Agents** | A second, independent agent that verifies the first agent's work | [CONCEPTS.md](CONCEPTS.md#sub-agents) |
| **Memory & State** | A durable file outside any single conversation that persists information across runs | [CONCEPTS.md](CONCEPTS.md#memory--state) |

## Maturity Tiers

| Tier | Definition | File |
|------|-----------|------|
| **L1 (Report Only)** | Loop reads, observes, writes down — changes nothing | [CONCEPTS.md](CONCEPTS.md#l1-report-only) |
| **L2 (Assisted)** | Loop proposes narrow-scope changes; human merges | [CONCEPTS.md](CONCEPTS.md#l2-assisted--patch-only) |
| **L3 (Unattended)** | Loop commits/merges/deploys autonomously | [CONCEPTS.md](CONCEPTS.md#l3-unattended) |

## Production Patterns

| Pattern | Definition | File |
|---------|-----------|------|
| **Daily Triage** | Once-daily categorization of issues and PRs | [PATTERNS.md](PATTERNS.md#daily-triage) |
| **PR Babysitter** | Frequent monitoring of pull requests | [PATTERNS.md](PATTERNS.md#pr-babysitter) |
| **CI Sweeper** | Frequent checking of CI build status | [PATTERNS.md](PATTERNS.md#ci-sweeper) |
| **Dependency Sweeper** | Periodic checking for outdated dependencies | [PATTERNS.md](PATTERNS.md#dependency-sweeper) |
| **Changelog Drafter** | Drafting changelogs from git history | [PATTERNS.md](PATTERNS.md#changelog-drafter) |
| **Post-Merge Cleanup** | Cleaning up after merges | [PATTERNS.md](PATTERNS.md#post-merge-cleanup) |

## Failure Modes

| Mode | Definition | File |
|------|-----------|------|
| **Verification stays on human** | Agent claims "done" without independent verification | [FAILURE-MODES.md](FAILURE-MODES.md#1-verification-stays-on-the-human) |
| **Comprehension debt** | Code ships faster than humans can read it | [FAILURE-MODES.md](FAILURE-MODES.md#2-comprehension-debt) |
| **Cognitive surrender** | Human accepts output without judgment | [FAILURE-MODES.md](FAILURE-MODES.md#3-cognitive-surrender) |
| **Token cost spikes** | Unexpected increases in token consumption | [FAILURE-MODES.md](FAILURE-MODES.md#4-token-cost-spikes) |
| **Multi-loop collisions** | Two loops touch the same files uncoordinated | [FAILURE-MODES.md](FAILURE-MODES.md#5-multi-loop-collisions) |
| **Agent grades its own work** | Same model does work and verifies it | [FAILURE-MODES.md](FAILURE-MODES.md#6-the-agent-grades-its-own-work) |

## Key Terms (Alphabetical)

See [TERMINOLOGY.md](TERMINOLOGY.md) for complete definitions.

| Term | Quick Definition |
|------|-----------------|
| AGENTS.md | House rules for agent behavior in a repo |
| Cadence | How frequently a loop runs |
| Kill switch | Mechanism to immediately stop a running loop |
| LLM | Large Language Model (GPT, Claude, etc.) |
| MCP | Model Context Protocol — standard for connecting agents to tools |
| Maker/Checker | Pattern where one agent produces work, another verifies it |
| SKILL.md | Project conventions file for agents |
| STATE.md | Persistent memory file across agent runs |
| VISION.md | What agents should be building toward |

---

*This index is maintained as part of the "Everything About Loop Engineering" repository. See [HONESTY.md](../HONESTY.md) for transparency about the field's age.*
