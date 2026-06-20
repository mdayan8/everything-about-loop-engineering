# Skill: Security Scanner

> **Usage:** Scans for hardcoded secrets and insecure configurations.

---

## Project Conventions

- **Type:** Report-only loop (L1)
- **Output:** Markdown report in `reports/security-scan.md`
- **Frequency:** Daily or on every commit
- **Token cost:** ~$0.10/run

## CRITICAL RULE

**Never expose found secrets in the report.** Use redacted placeholders:
- `password: [REDACTED]`
- `api_key: [REDACTED]`
- `token: [REDACTED]`

The report should indicate THAT a secret was found and WHERE, 
but never the actual value.
