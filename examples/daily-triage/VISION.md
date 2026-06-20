# Vision: Daily Triage

> Give the team a single daily snapshot of what needs attention across all open issues and pull requests.

---

## The Goal

Every morning, before standup, the team has an up-to-date summary of:
- How many issues are open, and which are urgent
- How many PRs are open, which are blocked, and which need review
- What's stale (no activity in 7+ days)
- What's new since yesterday

## Current State

Triage is done manually, inconsistently. Some days it happens, some days it doesn't. Stale issues accumulate. PRs sit unreviewed. The team doesn't have a single source of truth for "what needs attention today."

## Priorities

1. Generate a daily triage report automatically
2. Categorize issues by priority, age, and label
3. Flag stale issues (7+ days with no activity)
4. Flag PRs with failing CI, missing reviews, or merge conflicts

## Non-Goals

- This loop does NOT close issues
- This loop does NOT assign issues to people
- This loop does NOT merge PRs
- This loop does NOT modify any source code

## How Agents Should Use This File

This file anchors the triage loop's work. Every run should produce a report that matches these priorities. If the report is missing any of these sections, the loop should add it in the next run.
