# Project 03: Security Scanner

> Build a loop that catches hardcoded secrets and security issues.

---

## Goal

Run a loop that scans for hardcoded passwords, API keys, tokens, and insecure configurations.

## What This Loop Does

1. Scans for hardcoded secrets (passwords, API keys, tokens)
2. Checks for insecure configurations (debug mode, verbose errors)
3. Identifies files with sensitive data that should be in .env
4. Writes a security report to `reports/security-scan.md`
5. Updates `STATE.md`

## What This Loop Never Does

- Never exposes found secrets in logs
- Never modifies source code
- Never creates commits

## Setup

```bash
cd /path/to/your-repo
cp -r /path/to/everything-about-loop-engineering/projects/project-03-security-scanner/* .
mkdir -p reports
```

## Run

```bash
claude --prompt-file prompt.md
```

## Success Criteria

- [ ] `reports/security-scan.md` exists
- [ ] Report identifies any hardcoded secrets (or confirms none found)
- [ ] Report checks for insecure configurations
- [ ] `STATE.md` is updated
- [ ] No secrets are exposed in the report (use redacted placeholders)
