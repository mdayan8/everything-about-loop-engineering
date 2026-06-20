# Token Economics

> **Why costs spike, how to budget, and when the loop isn't worth the tokens.**

---

## How Token Costs Work

Every agent action costs tokens. Tokens are units of text processed by the model. The cost depends on:

- **Input tokens** — the prompt, context files, and conversation history
- **Output tokens** — the agent's response
- **Model** — different models have different per-token costs
- **Frequency** — how often the loop runs

A single loop run might cost $0.01–$0.10. But multiply by frequency and sub-agent fanout, and costs add up fast.

---

## Why Costs Spike

### 1. Sub-Agent Fanout

A single loop with 3 sub-agents costs roughly 4x the tokens of a single-agent loop (1 maker + 3 checkers). Each sub-agent reads the full context and produces its own output.

```
Single agent:   1x tokens
+1 sub-agent:   ~2x tokens
+3 sub-agents:  ~4x tokens
```

### 2. Large Context Windows

If the loop processes large files (entire codebases, long conversation histories), the input token count grows. A loop that reads 100 files costs 100x more than one that reads 1 file.

### 3. Infinite Retry Loops

If the loop's verification fails repeatedly, it may retry indefinitely. A loop that retries 10 times costs 10x more than one that succeeds on the first try.

### 4. Inefficient Prompts

Verbose prompts, unnecessary context, and redundant instructions waste input tokens. A well-crafted prompt is not just better engineering — it's cheaper.

---

## Budgeting Strategies

### 1. Set Hard Spend Caps

The most important control. Set a daily or monthly token budget for each loop. If the budget is exceeded, the loop stops.

### 2. Use the Right Model

Not every sub-agent needs the most powerful model. The maker might use a large model; the checker might use a smaller, cheaper model for simple verification.

### 3. Limit Context

Only pass the files and data the loop actually needs. Don't dump the entire codebase into the prompt when the loop only needs to check one file.

### 4. Monitor and Alert

Track token usage per loop. Set alerts for unusual spikes. A loop that normally costs $0.50/day and suddenly costs $5.00/day needs investigation.

### 5. Start at L1

L1 loops (report-only) are the cheapest. They read files and write reports. L2 and L3 loops do more work and cost more. Start cheap, increase complexity only when the value is proven.

---

## Cost Estimation Framework

| Pattern | Cadence | Est. Cost/Day | Est. Cost/Month |
|---------|---------|---------------|-----------------|
| Daily Triage (L1) | 1x/day | $0.05–$0.20 | $1.50–$6.00 |
| Changelog Drafter (L1) | 1x/day | $0.05–$0.15 | $1.50–$4.50 |
| Dependency Sweeper (L2) | 4x/day | $0.20–$0.80 | $6.00–$24.00 |
| PR Babysitter (L1) | 96x/day | $0.50–$2.00 | $15.00–$60.00 |
| CI Sweeper (L2) | 96x/day | $1.00–$5.00 | $30.00–$150.00 |

These are rough estimates. Actual costs depend on model, context size, and task complexity.

---

## When the Loop Isn't Worth the Tokens

A loop is not worth the cost when:
- The human can do the task faster than the loop can process it
- The loop's output requires so much human review that the time savings are negative
- The token cost exceeds the value of the task being automated
- The loop is running but nobody reads the output

**The loop exists to serve the human. If it's not serving the human, it's wasting tokens.**

---

## Try It Yourself

**Goal:** Estimate the cost of your loop portfolio.

**Steps:**
1. For each loop you run, estimate: tokens per run, runs per day, cost per run.
2. Calculate daily and monthly cost.
3. Compare to the value the loop provides (time saved, issues caught, etc.).
4. Identify any loops where cost exceeds value.

**Success condition:** You have a cost estimate for each loop and can justify the expense based on the value provided.

---

**Previous:** [Multi-Loop Coordination](multi-loop-coordination.md)
**Next:** [Beyond Coding](beyond-coding.md)
