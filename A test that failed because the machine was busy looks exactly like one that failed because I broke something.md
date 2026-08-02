---
type: Opportunity
source: >-
  INBOX:friction/2026-08-01-friction-wall-clock-budget-test-flaked-a-second-time-2280.md
created: '2026-08-02'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion
[[Budget against a same-run baseline instead of against the clock]]
[[Assert on work units instead of milliseconds]]
[[Re-run once and report the disagreement rather than the first result]]
[[My performance gate is an absolute number, so a busy machine alone can fail it]]

**The need (operator's voice):** "My gate went red. I cannot tell from the record whether I broke the product or whether the box was busy, so I have to re-run it by hand to find out — and if I stop bothering to check, the day it means something I will wave it through."

**What was observed (two confirmed occurrences):** `test/mcp/wall-clock-budget.test.ts` asserts a hard-coded millisecond ceiling. On the twentieth scheduled pass `ost_next_work` took 2004ms against a 2000ms budget inside the full 141-file suite, then passed at 18077ms of margin re-run in isolation seconds later. On the twenty-first pass the same test failed again at 2280ms and again passed in isolation. Same shape, same cause both times: zero tolerance for suite-level CPU contention on a shared sandbox, with no code regression behind either failure.

**Why it matters:** The whole value of an unattended gate is that its verdict can be trusted without a human re-deriving it. A threshold that fires on machine load spends the operator's scarcest resource — attention they do not have (see [[I need the tree's output to be actionable by compute alone, because my hours don't exist]]) — and it trains the reader to discount red. The second occurrence is what makes this an opportunity rather than a one-off: the twentieth pass's own filing named a repeat as the thing worth a human's eye rather than routine re-filing.

**Distinct from its neighbours:** [[My tests carry thresholds nobody ever fixed, so nothing can come out a failure]] is the absence of a committed threshold, so nothing can come out red. This is the opposite failure — a threshold that is committed but not robust, so red carries no information. [[A failed pass reports success, so my automation can't tell]] is a false pass; this is a false fail.

**Litmus test:** More than one way to address it — express the budget as margin relative to a same-run baseline rather than absolute wall-clock; assert on work units (calls, file reads) instead of time; retry-and-confirm before reporting red; record machine load alongside the verdict so a reader can attribute it; isolate timing-sensitive tests from the contended suite; quarantine the assertion into a separate advisory lane. Real trade-offs between them. Passes.

**Evidence rung:** `assertion` — the source is the agent's own friction filing. No external party involved; floor rung per the ladder's rule.

## Evidence — the first occurrence (mapped 2026-08-02)

`INBOX:friction/2026-08-01-friction-wall-clock-budget-test-flaked-once-ost-next-work.md` — kind `slow`, filed 19:30Z, one hour before the filing this node is sourced to. `ost_next_work` took 2004ms against the 2000ms budget inside the full 141-file suite, then passed at 18077ms of margin re-run in isolation seconds later. Filed with the cause already correctly identified: "a hard-coded ms threshold with no tolerance for suite-level CPU contention, so it can fail on a shared sandbox without any code regression."

The pair matters more than either filing alone. A single flake is noise a reasonable person ignores; two in consecutive passes, with the same test, the same shape and the same isolation-passes result, is a property of the gate rather than of the machine. The twentieth pass's filing pre-committed the escalation — a second occurrence was to be treated as worth a human's eye rather than routine re-filing — and the twenty-first delivered it. That pre-commitment is why this reached the tree instead of becoming a third identical friction note.
