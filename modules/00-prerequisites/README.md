# Module 00: Prerequisites

> **What you need before starting this course — and what you don't.**

---

## What You Need

### Basic Command Line

You should be comfortable with:
- Opening a terminal
- Navigating directories (`cd`, `ls`)
- Running commands
- Reading output and error messages

You do not need to be a power user. If you can navigate to a folder and run a command, you have enough.

### Basic Git

You should understand:
- What a git repository is
- How to clone a repo (`git clone`)
- How to check status (`git status`)
- How to add and commit files (`git add`, `git commit`)
- What a branch is (conceptually)

You do not need to be a git expert. Branching, merging, and rebasing will be explained as they become relevant.

### Access to a Coding Agent

You need access to at least one of the following:
- **Claude Code** — Anthropic's terminal-based coding agent
- **Codex** — OpenAI's coding agent
- **Another agent** with filesystem access and the ability to run shell commands

Both Claude Code and Codex are the primary tools referenced in this course because they shipped the core loop engineering features (scheduling, worktrees, sub-agents) natively as of mid-2026.

If you do not have access yet, check the documentation for your preferred tool to set it up before proceeding.

### A Text Editor

Any text editor that can edit markdown files. VS Code, Vim, Nano, or the built-in editor that comes with your coding agent all work.

---

## What You Do Not Need

- **No coding-agent experience required.** Modules 01–02 explain what agents are from scratch.
- **No programming language knowledge required.** The templates and exercises in this course are markdown-based. You will not write production code.
- **No paid tools required.** The core concepts apply to any agent with file access. Templates are plain markdown.
- **No prior knowledge of loop engineering required.** That's what this course teaches.

---

## Setup Check

Run these commands to verify your environment is ready:

```bash
# Check git is installed
git --version

# Check you can create a directory and navigate to it
mkdir -p /tmp/loop-engineering-test
cd /tmp/loop-engineering-test
pwd

# Check you can create and edit a file
echo "# Test" > test.md
cat test.md

# Clean up
cd ~
rm -rf /tmp/loop-engineering-test
```

If all of those work, you are ready to begin.

---

## How This Course Is Structured

The modules are sequential. Each one builds on the previous:

| Module | What You Learn |
|--------|----------------|
| [00 — Prerequisites](README.md) | What you need before starting |
| [01 — What is an AI Coding Agent](../01-what-is-an-ai-coding-agent/README.md) | Agents, prompts, and prompt engineering |
| [02 — What is Loop Engineering](../02-what-is-loop-engineering/README.md) | The discipline, its history, and its core idea |
| [03 — The Five Building Blocks](../03-the-five-building-blocks/README.md) | The components that make up a loop |
| [04 — Building Your First Loop](../04-building-your-first-loop/README.md) | Hands-on: build and run a real loop |
| [05 — The Maturity Model](../05-the-maturity-model/README.md) | L1, L2, L3 — and when to advance |
| [06 — Production Patterns](../06-production-patterns/README.md) | Six battle-tested loop patterns |
| [07 — What Goes Wrong](../07-what-goes-wrong/README.md) | Failure modes and how to prevent them |
| [08 — The Skeptics' Case](../08-the-skeptics-case/README.md) | The honest counterarguments |
| [09 — Advanced Topics](../09-advanced-topics/README.md) | Multi-loop coordination, token economics, beyond coding |
| [10 — Capstone Project](../10-capstone-project/README.md) | Design and document a real loop |

**Start here, go in order for modules 00–04.** After that, modules are reference material you can return to as needed.

---

## Try It Yourself

**Goal:** Confirm your environment is ready.

**Steps:**
1. Open a terminal.
2. Run `git --version` — confirm git is installed.
3. Run `mkdir -p /tmp/loop-test && cd /tmp/loop-test && echo "# Test" > test.md && cat test.md` — confirm you can create and read files.
4. Confirm you have access to a coding agent (Claude Code, Codex, or equivalent).

**Success condition:** All four checks pass. You see the git version number, the test file content, and you can open your coding agent.

---

**Next:** [Module 01 — What is an AI Coding Agent](../01-what-is-an-ai-coding-agent/README.md)
