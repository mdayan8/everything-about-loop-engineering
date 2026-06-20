# Examples

Worked examples demonstrating loop engineering patterns in practice.

---

## What's Here

| Example | Pattern | Maturity | Description |
|---------|---------|----------|-------------|
| [Daily Triage](daily-triage/) | Daily Triage | L1 | Categorizes issues and PRs, writes a daily snapshot |
| [Changelog Drafter](changelog-drafter/) | Changelog Drafter | L1 | Drafts a changelog from git history |
| [Code Quality Guardian](code-quality-guardian/) | Multi-Sub-Agent | L1 | Four independent sub-agents verify quality in parallel |

---

## How to Use These Examples

1. **Read the files.** Each example includes a SKILL.md, VISION.md, AGENTS.md, and STATE.md. Read them to understand the conventions and rules.
2. **Adapt, don't copy.** These are illustrations, not production configs. Your actual loop will need to be tailored to your project.
3. **Start with Changelog Drafter.** It's the lowest-risk, lowest-cost pattern and the recommended first loop.
4. **Follow the maturity model.** Both examples are L1 (report only). Don't jump to L2 without reading [Module 05](../modules/05-the-maturity-model/README.md).

---

## Running the Examples

### Changelog Drafter

```bash
# Clone the repo you want to draft a changelog for
cd /path/to/your-repo

# Copy the example files
cp -r /path/to/everything-about-loop-engineering/examples/changelog-drafter/* .

# Run the loop (using Claude Code as an example)
claude --prompt-file prompts/changelog-drafter.md

# Check the output
cat reports/changelog-draft.md
```

### Daily Triage

```bash
# Set your GitHub token
export GITHUB_TOKEN=your-token-here
export GITHUB_REPO=owner/repo

# Copy the example files
cp -r /path/to/everything-about-loop-engineering/examples/daily-triage/* .

# Run the loop
claude --prompt-file prompts/triage.md

# Check the output
cat reports/triage.md
```

---

## Creating Your Own Examples

After running these examples, create your own:

1. Fill out the design canvas: [templates/first-loop-design-canvas.md](../templates/first-loop-design-canvas.md)
2. Create SKILL.md, VISION.md, AGENTS.md, STATE.md
3. Run the loop at L1 for at least 3 days
4. Document what worked and what didn't
5. Share your example with the community

---

## Feedback

If you run one of these examples and find issues, please [open an issue](../../issues) or [submit a correction](../CONTRIBUTING.md).
