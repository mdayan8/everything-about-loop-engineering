# Skill: Doc Generator

> **Usage:** Generates API documentation from source code.

---

## Project Conventions

- **Type:** Report-only loop (L1)
- **Output:** Markdown documentation in `reports/api-docs.md`
- **Frequency:** On code change or daily
- **Token cost:** ~$0.15/run

## What This Loop Does

1. Reads source files
2. Extracts function/class signatures
3. Parses docstrings and type hints
4. Generates structured documentation
5. Writes to reports/

## What This Loop Must Never Do

- Never modifies source code
- Never creates commits
- Never deletes existing documentation
