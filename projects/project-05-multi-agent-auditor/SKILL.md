# Skill: Multi-Agent Auditor

> **Usage:** Runs 4 independent sub-agents to audit a repository in parallel.

---

## Project Conventions

- **Type:** Multi-sub-agent loop (L1) — report only
- **Output:** 4 individual reports + 1 combined report
- **Frequency:** Weekly or on-demand
- **Token cost:** ~$0.30/run (4 sub-agents + orchestrator)

## Sub-Agent Roles

| Sub-Agent | Checks | Report |
|-----------|--------|--------|
| Link Checker | Internal markdown links | reports/link-check.md |
| Structure Auditor | Directory structure | reports/structure-audit.md |
| Content Checker | Required sections in docs | reports/content-check.md |
| Style Linter | Markdown formatting | reports/style-lint.md |

## Combined Report

The orchestrator combines all findings into `reports/multi-agent-audit.md`.
