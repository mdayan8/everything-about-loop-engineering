# Vision: Code Quality Guardian

> Automatically verify that every module, template, and example in this repository is complete, consistent, and accurate.

---

## The Goal

Every run produces a report answering:
1. Are all internal links valid?
2. Is the directory structure complete per the spec?
3. Do all modules have the required sections (intro, concept, diagram, example, exercise)?
4. Are glossary terms used consistently across modules?

## Current State

Quality is verified manually. Links may break as files move. Modules may drift from the required structure. Glossary terms may be used inconsistently.

## Priorities

1. Detect broken internal links
2. Verify directory structure matches the spec
3. Check module structure compliance
4. Verify glossary term consistency

## Non-Goals

- This loop does NOT modify source files
- This loop does NOT create commits
- This loop does NOT fix issues — it reports them

## How Agents Should Use This File

This file anchors the guardian's work. Every run should check all four domains. If any check is skipped, the report should note the omission.
