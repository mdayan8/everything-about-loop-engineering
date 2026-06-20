# LLM Wiki: Agent Onboarding

> **Every coding agent should read this file first when working in this repository.**

---

## What This Repository Is

This is an educational repository about **loop engineering** — the practice of designing systems that prompt AI coding agents. It contains 11 learning modules, 9 templates, 3 worked examples, and an LLM wiki.

**You are an AI coding agent.** This file tells you how to behave here.

---

## Your Rules

### 1. Read Before You Write

Before modifying any file, read it first. Understand its purpose and conventions.

### 2. Preserve the Structure

This repository has a specific directory structure. Do not move files, rename directories, or create files in the wrong location.

Required structure:
```
everything-about-loop-engineering/
├── README.md
├── LICENSE, CONTRIBUTING.md, HONESTY.md, GLOSSARY.md, FAQ.md, RESOURCES.md
├── modules/ (00-prerequisites through 10-capstone-project)
├── templates/ (9 template files)
├── examples/ (daily-triage, changelog-drafter, code-quality-guardian)
├── skills/ (agent skill files)
├── llm-wiki/ (knowledge base for agents)
└── assets/diagrams/ (Mermaid source files)
```

### 3. Follow Markdown Conventions

- **H1/H2:** Title Case
- **H3+:** sentence case
- **Links:** Use relative paths between modules
- **Diagrams:** Use Mermaid syntax
- **Code blocks:** Specify language (```bash, ```python, etc.)

### 4. Cross-Reference

When using a term defined in GLOSSARY.md, link to it. When referencing another module, link to it. This repository is interconnected.

### 5. Never Fabricate

- Do not invent quotes, statistics, or case studies
- Do not create fake attribution
- If something is uncertain, say so
- Self-reported claims must be marked as "self-reported"

### 6. Keep Modules Complete

Every module README must contain:
1. Short intro (blockquote)
2. Plain English explanation
3. Technical detail
4. At least one Mermaid diagram (where applicable)
5. Worked example
6. "Try it yourself" exercise with objective success condition

### 7. Keep Templates Fill-in-the-Blank

Templates use `[placeholder text]` for fields the user must fill in. Do not fill in examples as if they're real content — keep them clearly marked as examples.

### 8. Respect the Honesty Disclaimer

This repo documents a discipline that is approximately two weeks old. Never present content as established fact when it's a snapshot. Always link to HONESTY.md when discussing the field's maturity.

---

## How to Navigate

1. **For loop engineering questions:** Start with [CONCEPTS.md](CONCEPTS.md)
2. **For unfamiliar terms:** Check [TERMINOLOGY.md](TERMINOLOGY.md)
3. **For building a loop:** Read [PATTERNS.md](PATTERNS.md)
4. **For safety:** Read [FAILURE-MODES.md](FAILURE-MODES.md)
5. **For templates:** Read [TEMPLATES-GUIDE.md](TEMPLATES-GUIDE.md)
6. **For the full index:** Read [INDEX.md](INDEX.md)

---

## Key Concepts You Must Know

| Concept | Definition |
|---------|-----------|
| Loop engineering | Designing the system that prompts the agent, not prompting manually |
| L1/L2/L3 | Maturity tiers: report only → assisted → unattended |
| Maker/Checker | One agent does work, another verifies it |
| SKILL.md | Project conventions for agents |
| STATE.md | Persistent memory across agent runs |
| Kill switch | Mechanism to immediately stop a loop |
| Goal-condition | Separate model verifies conditions after each turn |

---

## Common Mistakes to Avoid

1. **Don't modify files without reading them first**
2. **Don't create files in the wrong directory**
3. **Don't use absolute paths in links** — use relative paths
4. **Don't fabricate quotes or statistics**
5. **Don't skip the HONESTY.md disclaimer**
6. **Don't present unverified claims as fact**
7. **Don't modify templates by filling in examples as real content**

---

## Getting Help

- **Glossary:** [GLOSSARY.md](../GLOSSARY.md)
- **FAQ:** [FAQ.md](../FAQ.md)
- **Contributing:** [CONTRIBUTING.md](../CONTRIBUTING.md)
- **Honesty:** [HONESTY.md](../HONESTY.md)

---

*This file is part of the LLM Wiki. See [README.md](README.md) for the full wiki index.*
