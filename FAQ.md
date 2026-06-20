# Frequently Asked Questions

---

## Getting Started

### Do I need coding experience to use this repo?

No. Modules 00–02 assume zero coding-agent experience. You should have basic command-line familiarity and basic git knowledge. Beyond that, no prerequisites.

### Which coding agent do I need?

This repo is tool-agnostic in principle but references Claude Code and OpenAI Codex most often, since those are the two products where the core features (scheduling, worktrees, sub-agents) shipped natively as of mid-2026. The concepts apply to any agent with filesystem access and scheduling capability.

### How long does it take to complete the course?

Modules 00–04 (through building your first loop) can be completed in a focused afternoon. Modules 05–10 are reference material you'll return to as your loops mature. The capstone project (Module 10) is a half-day exercise.

### What is the absolute minimum to get started?

A terminal, git, and access to Claude Code (or Codex). That's it. The templates are fill-in-the-blank. Your first loop can be report-only (L1) and cost almost nothing in tokens.

---

## Safety & Cost

### Are loops safe?

Loops at L1 (report only) are very safe — they read and write markdown, nothing else. L2 loops propose changes but require human review. L3 loops commit and deploy autonomously. Most loops should stay at L1 for a long time.

### How much do loops cost in tokens?

It depends on cadence, scope, and whether sub-agents are used. A daily triage loop (L1) is low-cost. A PR babysitter running every 5 minutes with sub-agent verification is high-cost. See [Module 09: Token Economics](modules/09-advanced-topics/token-economics.md) for budgeting guidance.

### Can a loop damage my codebase?

L1 loops cannot — they only write reports. L2 loops propose changes but you review them before merging. L3 loops can modify code autonomously, which is why the pre-flight checklist in [templates/loop-design-checklist.md](templates/loop-design-checklist.md) exists. Never enable L3 without proven guardrails.

### What about secrets and credentials?

Loops should never handle secrets directly. Use environment variables. A loop that needs API access should reference `process.env` or a secrets manager, never hardcode values. See the security checklist in [CONTRIBUTING.md](CONTRIBUTING.md).

---

## Tooling

### What is MCP?

Model Context Protocol (MCP) is a standard that lets AI agents connect to external tools — issue trackers, databases, chat platforms, deployment systems — beyond the filesystem. Plugins and connectors in loop engineering are built on MCP.

### Do I need to write code to build loops?

Not necessarily. The templates in this repo are fill-in-the-blank markdown. Your first loop can be configured with markdown files and a scheduling mechanism. More advanced loops may require scripting for custom verification logic.

### Can I use loops with non-Anthropic models?

Yes. The loop engineering pattern is model-agnostic. Sub-agents can use different models. The key requirement is that your agent tool supports scheduling and file access. Check your tool's documentation for worktree and automation support.

---

## Philosophy

### Isn't this just a while loop?

Partially — yes. The skeptics' case is covered fairly in [Module 08](modules/08-the-skeptics-case/README.md). The shape (control loop) is decades old. What's arguably new is the scaffolding (native scheduling, native worktrees, native sub-agents, native cross-session memory) that shipped simultaneously inside coding agent tools.

### Will this replace human programmers?

This repo doesn't take a position on that question. Loop engineering is a tool for making AI coding agents more effective. Whether that expands or contracts human roles depends on many factors outside the scope of this project.

### Is "loop engineering" a real discipline?

As of mid-June 2026, it's a named concept that is approximately two weeks old. It was coined by Addy Osmani building on work by Boris Cherny and Peter Steinberger. Whether it becomes an established discipline depends on how the practice evolves. See [HONESTY.md](HONESTY.md) for transparency about the field's age.

---

## Contributing

### How do I report an error?

Open an issue with the module name, the incorrect claim, and a source that contradicts it. See [CONTRIBUTING.md](CONTRIBUTING.md).

### Can I add my own case study?

Yes, but it must be clearly marked as self-reported and attributed to a verifiable source (your public writing, social media profile, or published project). We do not accept unattributed claims.

### Can I translate this repo?

Yes. MIT licensed. Attribution appreciated but not required.
