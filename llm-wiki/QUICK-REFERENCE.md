# LLM Wiki: Quick Reference

> One-page cheat sheet. Print this. Bookmark this. Use this.

---

## Loop Engineering in One Sentence

**Loop engineering is designing the system that prompts your AI coding agent, instead of typing each prompt yourself.**

---

## The Three Tiers

| Tier | What It Does | When to Use |
|------|-------------|-------------|
| **L1** | Report only — reads, observes, writes down | Most loops, most of the time |
| **L2** | Proposes changes — human merges | After L1 proven, narrow scope |
| **L3** | Autonomous — commits/merges/deploys | Rarely. Few tasks earn this. |

---

## The Six Building Blocks

1. **Automations** — Schedule/trigger the loop
2. **Worktrees** — Isolate parallel agents
3. **Skills** — Project conventions (SKILL.md)
4. **Plugins** — External tools (MCP)
5. **Sub-agents** — Independent verification
6. **Memory** — Persistent state (STATE.md)

---

## The Six Patterns

| Pattern | Cost | Starting Tier |
|---------|------|---------------|
| Daily Triage | Low | L1 |
| Changelog Drafter | Low | L1 |
| Post-Merge Cleanup | Low | L1 |
| Dependency Sweeper | Medium | L2 |
| PR Babysitter | High | L1 |
| CI Sweeper | Very high | L2 |

---

## Pre-Launch Checklist (L2+)

- [ ] Verifier sub-agent in place
- [ ] Spend cap set
- [ ] Kill switch tested
- [ ] Scope narrow enough
- [ ] Human review point defined
- [ ] Automated verification exists
- [ ] L1 running successfully for 1+ week
- [ ] Failure modes documented
- [ ] Rollback plan exists

---

## Failure Modes

1. **Verification on human** — Agent claims done, human checks everything
2. **Comprehension debt** — Code ships faster than humans read it
3. **Cognitive surrender** — Human accepts output without judgment
4. **Token cost spikes** — Unexpected token consumption
5. **Multi-loop collisions** — Two loops touch same files
6. **Self-grading** — Agent grades its own work

---

## Key Quotes

> "My job is to write loops." — Boris Cherny

> "You should be designing loops that prompt your agents." — Peter Steinberger

> "Build the loop. But build it like someone who intends to stay the engineer." — Addy Osmani

---

## Quick Links

| What You Need | Where to Look |
|---------------|--------------|
| Definition | [CONCEPTS.md](CONCEPTS.md) |
| Term | [TERMINOLOGY.md](TERMINOLOGY.md) |
| Pattern | [PATTERNS.md](PATTERNS.md) |
| What goes wrong | [FAILURE-MODES.md](FAILURE-MODES.md) |
| Template help | [TEMPLATES-GUIDE.md](TEMPLATES-GUIDE.md) |
| Agent rules | [AGENT-ONBOARDING.md](AGENT-ONBOARDING.md) |
| Full index | [INDEX.md](INDEX.md) |

---

## The Golden Rule

> **A loop only catches what you specifically taught it to check.**

---

*Part of the LLM Wiki. See [README.md](README.md) for the full wiki index.*
