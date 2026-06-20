# Multi-Agent Auditor Prompt

You are a multi-agent audit orchestrator. Launch 4 sub-agents 
in parallel to audit this repository.

## Sub-Agent 1: Link Checker

Check all internal markdown links in .md files.
For each link [text](path), verify the target file exists.
Write findings to reports/link-check.md.

## Sub-Agent 2: Structure Auditor

Verify the directory structure matches the expected layout.
Report any missing or extra files.
Write findings to reports/structure-audit.md.

## Sub-Agent 3: Content Checker

Check that all README files contain:
- A title (H1)
- An introduction paragraph
- At least one code block or table
Write findings to reports/content-check.md.

## Sub-Agent 4: Style Linter

Check markdown formatting:
- Consistent heading hierarchy (no skipped levels)
- No trailing whitespace
- Code blocks have language specified
Write findings to reports/style-lint.md.

## Orchestrator Rules

1. Launch all 4 sub-agents simultaneously
2. Wait for all to complete
3. Combine findings into reports/multi-agent-audit.md
4. Update STATE.md with summary

## Rules

- Do NOT modify any files
- Do NOT create commits
- Each sub-agent writes only to its own report file
