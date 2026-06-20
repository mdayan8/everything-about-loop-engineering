# Skill: Agent Onboarding

> **Usage:** Onboards any coding agent to this repository — tells it the rules, conventions, and how to navigate.

---

## Purpose

Every coding agent that works in this repository should read this skill first. It tells the agent:

1. What this repository is
2. How to behave
3. What to do and not do
4. Where to find information

## Skill Contents

When loaded, this skill provides:

### Repository Identity

- **Name:** Everything About Loop Engineering
- **Type:** Educational repository (learning resource, not software)
- **Language:** Markdown
- **License:** MIT
- **Field age:** ~2 weeks as of mid-June 2026

### Agent Rules

1. **Read before you write** — never modify a file without reading it first
2. **Preserve the structure** — don't move files or rename directories
3. **Follow markdown conventions** — H1/H2 Title Case, H3+ sentence case
4. **Cross-reference** — link to glossary terms and other modules
5. **Never fabricate** — no invented quotes, statistics, or case studies
6. **Keep modules complete** — every module needs: intro, explanation, diagram, example, exercise
7. **Keep templates fill-in-the-blank** — don't fill in examples as real content
8. **Respect the honesty disclaimer** — this is a young field, not established practice

### Directory Map

```
├── modules/          → 11 learning modules (00-prerequisites through 10-capstone)
├── templates/        → 9 fill-in-the-blank templates
├── examples/         → 3 worked examples (daily-triage, changelog-drafter, code-quality-guardian)
├── skills/           → Agent skill files for different patterns
├── llm-wiki/         → Knowledge base for AI agents
├── assets/diagrams/  → Mermaid diagram source files
├── GLOSSARY.md       → Term definitions
├── FAQ.md            → Frequently asked questions
├── RESOURCES.md      → Attributed sources
├── CONTRIBUTING.md   → How to contribute
└── HONESTY.md        → Transparency about the field
```

### Key Concepts

| Concept | Where to Learn |
|---------|---------------|
| What is loop engineering? | `modules/02-what-is-loop-engineering/README.md` |
| The five building blocks | `modules/03-the-five-building-blocks/README.md` |
| How to build a loop | `modules/04-building-your-first-loop/README.md` |
| The maturity model | `modules/05-the-maturity-model/README.md` |
| Production patterns | `modules/06-production-patterns/README.md` |
| What goes wrong | `modules/07-what-goes-wrong/README.md` |

### Common Mistakes

1. Using absolute paths in links (use relative paths)
2. Creating files in the wrong directory
3. Presenting unverified claims as fact
4. Skipping the HONESTY.md disclaimer
5. Filling in templates with real content (keep them as templates)

### For Agent Developers

To use this skill in your coding agent:

1. Copy this file to your agent's knowledge base
2. Add it to your agent's system prompt or skill registry
3. The agent will load it when working in this repository

The skill is self-contained — no external dependencies required.
