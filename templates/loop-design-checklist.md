# Loop Design Pre-Flight Checklist

> Complete this checklist before enabling any L2+ loop. For L1 loops, items marked [L1 REQUIRED] are mandatory; others are recommended.

---

## Verification

- [ ] **[L1 REQUIRED]** Verifier sub-agent is in place — independent verification, not self-assessment
- [ ] **[L1 REQUIRED]** Objective success criteria are defined — the loop can determine "done" without human judgment
- [ ] **[L1 REQUIRED]** Automated verification exists — tests, linting, schema validation, or equivalent

## Safety

- [ ] **[L1 REQUIRED]** Spend cap is set — hard limit on token consumption
- [ ] **[L1 REQUIRED]** Kill switch is tested — you can stop the loop immediately
- [ ] **[L1 REQUIRED]** Scope is narrow enough for current tier — one type of change, well-defined
- [ ] Rollback plan exists — you can undo the loop's changes if needed

## History

- [ ] **L1→L2:** L1 has run successfully for at least 1 week
- [ ] **L2→L3:** L2 has run successfully for at least 2 weeks
- [ ] **L2→L3:** Output is consistently accurate (no false positives in the last 2 weeks)
- [ ] **L2→L3:** Failure modes are understood and documented

## Coordination

- [ ] File ownership is defined — which files does this loop touch?
- [ ] Multi-loop conflicts are identified — do other loops touch the same files?
- [ ] Schedule overlaps are resolved — do other loops run at the same time?

## Human Review

- [ ] **[L1 REQUIRED]** Human review point is defined — where does the human check the output?
- [ ] **[L1 REQUIRED]** Output is readable — the human can quickly assess correctness
- [ ] Escalation path exists — what happens when the loop finds something it can't handle?

---

## Sign-Off

- **Loop name:** [name]
- **Current tier:** [L1 / L2 / L3]
- **Checked by:** [name]
- **Date:** [date]
- **Notes:** [any gaps or concerns]
