# Projects: Hands-On Loop Engineering

> **Practice loops by building real ones.** Each project is a complete, runnable loop you can deploy in minutes.

---

## How These Projects Work

1. **Pick a project** based on your experience level
2. **Clone or copy** the starter files into your own repo
3. **Configure** the few fields marked `[FILL IN]`
4. **Run the loop** using Claude Code, Codex, or the GitHub Actions workflow
5. **Check the output** — verify the loop did what it should
6. **Iterate** — improve the prompt, add verification, increase maturity

Each project includes:
- A `SKILL.md` — what the loop does and doesn't do
- A `prompt.md` — the exact prompt the agent receives
- A `STATE.md` — persistent memory across runs
- A `config.yml` — GitHub Actions workflow (copy to `.github/workflows/`)
- A `README.md` — step-by-step instructions

---

## Projects by Difficulty

| # | Project | Difficulty | Cost | What You Build |
|---|---------|-----------|------|----------------|
| 01 | [Hello Loop](project-01-hello-loop/) | Beginner | ~$0.01 | Your first L1 report-only loop |
| 02 | [Dependency Checker](project-02-dependency-checker/) | Beginner | ~$0.05 | Checks for outdated dependencies |
| 03 | [Security Scanner](project-03-security-scanner/) | Intermediate | ~$0.10 | Scans for hardcoded secrets |
| 04 | [Doc Generator](project-04-doc-generator/) | Intermediate | ~$0.15 | Generates API docs from code |
| 05 | [Multi-Agent Auditor](project-05-multi-agent-auditor/) | Advanced | ~$0.30 | 4 sub-agents auditing in parallel |

---

## Project 01: Hello Loop (Start Here)

**Goal:** Run your first loop. See it work. Understand the pattern.

**What it does:** Reads your git log, counts commits by author, and writes a report.

**Time:** 5 minutes to set up, runs forever.

**Files:**
```
project-01-hello-loop/
├── README.md          # Step-by-step instructions
├── SKILL.md           # Agent conventions
├── prompt.md          # The prompt the agent receives
├── STATE.md           # Persistent memory
└── config.yml         # GitHub Actions workflow
```

---

## Project 02: Dependency Checker

**Goal:** Build a loop that catches outdated dependencies before they become vulnerabilities.

**What it does:** Checks npm/pip/go dependencies, categorizes updates, proposes safe ones.

**Time:** 10 minutes to set up.

**Files:**
```
project-02-dependency-checker/
├── README.md
├── SKILL.md
├── prompt.md
├── STATE.md
└── config.yml
```

---

## Project 03: Security Scanner

**Goal:** Build a loop that catches hardcoded secrets and security issues.

**What it does:** Scans for hardcoded passwords, API keys, tokens, and insecure configurations.

**Time:** 15 minutes to set up.

**Files:**
```
project-03-security-scanner/
├── README.md
├── SKILL.md
├── prompt.md
├── STATE.md
└── config.yml
```

---

## Project 04: Doc Generator

**Goal:** Build a loop that keeps documentation in sync with code.

**What it does:** Reads source code, extracts function signatures, generates API docs.

**Time:** 15 minutes to set up.

**Files:**
```
project-04-doc-generator/
├── README.md
├── SKILL.md
├── prompt.md
├── STATE.md
└── config.yml
```

---

## Project 05: Multi-Agent Auditor

**Goal:** Build a loop with 4 independent sub-agents running in parallel.

**What it does:** Links, structure, content, and consistency checked simultaneously.

**Time:** 20 minutes to set up.

**Files:**
```
project-05-multi-agent-auditor/
├── README.md
├── SKILL.md
├── prompt.md
├── STATE.md
├── subagent-link-checker.md
├── subagent-structure.md
├── subagent-content.md
├── subagent-consistency.md
└── config.yml
```

---

## After You Complete a Project

1. **Share it** — open a PR or issue showing your results
2. **Improve it** — add verification, increase maturity, reduce cost
3. **Combine projects** — run multiple loops on the same repo
4. **Build your own** — use the [Loop Designer skill](../skills/loop-designer.md) to design a loop for your real project

---

## Quick Start (Project 01)

```bash
# 1. Go to any git repository
cd /path/to/your-repo

# 2. Copy the project files
cp -r /path/to/everything-about-loop-engineering/projects/project-01-hello-loop/* .

# 3. Run the loop (Claude Code example)
claude --prompt-file prompt.md

# 4. Check the output
cat reports/hello-loop-report.md

# 5. Check the state
cat STATE.md
```

---

*See [Module 04: Building Your First Loop](../modules/04-building-your-first-loop/README.md) for the full walkthrough. See [skills/loop-designer.md](../skills/loop-designer.md) for help designing your own loop.*
