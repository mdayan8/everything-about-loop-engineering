# LLM Wiki: Loop Engineering Knowledge Base

> **This directory is a structured knowledge base designed for AI agents and coding agents to ingest.** Any agent can read these files to understand loop engineering without human explanation.

---

## How to Use This Wiki

**For humans:** Read these files to get a comprehensive understanding of loop engineering. Cross-reference with the [modules](../modules/) for deeper dives.

**For AI agents:** Read `INDEX.md` first. It maps every concept to its definition. Then read the specific file related to your task. Every file is self-contained — you don't need to read them in order.

**For coding agent onboarding:** Start with `AGENT-ONBOARDING.md`. It tells you exactly how to behave in this repository.

---

## Files

| File | Purpose | When to Read |
|------|---------|-------------|
| [INDEX.md](INDEX.md) | Master index of all concepts | First — always |
| [CONCEPTS.md](CONCEPTS.md) | Core concepts with definitions | When you need to understand what something means |
| [TERMINOLOGY.md](TERMINOLOGY.md) | Every term, its definition, and usage | When you encounter an unfamiliar term |
| [PATTERNS.md](PATTERNS.md) | All production patterns with configs | When you need to build or modify a loop |
| [FAILURE-MODES.md](FAILURE-MODES.md) | What goes wrong and how to prevent it | Before enabling any L2+ loop |
| [TEMPLATES-GUIDE.md](TEMPLATES-GUIDE.md) | How to use every template in this repo | When filling out templates |
| [AGENT-ONBOARDING.md](AGENT-ONBOARDING.md) | How any coding agent should behave here | First thing an agent reads |
| [QUICK-REFERENCE.md](QUICK-REFERENCE.md) | One-page cheat sheet | When you need a fast answer |

---

## For Agent Developers

If you're building a coding agent and want it to understand loop engineering:

1. Copy this `llm-wiki/` directory into your agent's knowledge base
2. Point your agent's system prompt to `AGENT-ONBOARDING.md`
3. The agent can then read any other file as needed

The files are plain Markdown, no special formatting required. They work with any LLM.
