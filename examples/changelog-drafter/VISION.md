# Vision: Changelog Drafter

> Automatically produce a draft changelog from git history so no meaningful change is forgotten.

---

## The Goal

Every release (or daily), the team has a draft changelog that:
- Categorizes all commits by type (feat, fix, docs, chore, etc.)
- Groups related changes together
- Highlights breaking changes
- Links to relevant issues and PRs

## Current State

Changelogs are written manually, often after the fact. Commits are forgotten. The changelog is incomplete or inaccurate. The team spends time reconstructing what changed instead of writing the changelog as changes happen.

## Priorities

1. Draft the changelog from git history automatically
2. Categorize commits by type
3. Group related changes
4. Flag breaking changes

## Non-Goals

- This loop does NOT modify source code
- This loop does NOT create commits
- This loop does NOT publish the changelog
- This loop does NOT modify git history

## How Agents Should Use This File

This file anchors the changelog drafter's work. Every run should produce a draft changelog that follows these conventions. If the draft is missing categories or groups, the loop should fix it in the next run.
