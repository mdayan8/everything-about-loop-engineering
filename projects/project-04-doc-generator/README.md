# Project 04: Doc Generator

> Build a loop that keeps documentation in sync with code.

---

## Goal

Run a loop that reads source code, extracts function signatures, and generates API documentation.

## What This Loop Does

1. Reads source files (Python, TypeScript, Go, etc.)
2. Extracts function/class signatures and docstrings
3. Generates API documentation in markdown
4. Writes docs to `reports/api-docs.md`
5. Updates `STATE.md`

## What This Loop Never Does

- Never modifies source code
- Never creates commits
- Never deletes existing documentation

## Setup

```bash
cd /path/to/your-repo
cp -r /path/to/everything-about-loop-engineering/projects/project-04-doc-generator/* .
mkdir -p reports
```

## Run

```bash
claude --prompt-file prompt.md
```

## Success Criteria

- [ ] `reports/api-docs.md` exists
- [ ] Docs include function signatures
- [ ] Docs include parameter descriptions
- [ ] Docs include return types
- [ ] `STATE.md` is updated
- [ ] No source code was modified
