---
type: Opportunity
source: >-
  INBOX:friction/2026-08-01-friction-wall-clock-budget-test-flaked-a-second-time-2280.md
created: '2026-08-02'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion

**The need (operator's voice):** "My gate went red. I cannot tell from the record whether I broke the product or whether the box was busy, so I have to re-run it by hand to find out — and if I stop bothering to check, the day it means something I will wave it through."

**What was observed (two confirmed occurrences):** `test/mcp/wall-clock-budget.test.ts` asserts a hard-coded millisecond ceiling. On the twentieth scheduled pass `ost_next_work` took 2004ms against a 2000ms budget inside the full 141-file suite, then passed at 18077ms of margin re-run in isolation seconds later. On the twenty-first pass the same test failed again at 2280ms and again passed in isolation. Same shape, same cause both times: zero tolerance for suite-level CPU contention on a shared sandbox, with no code regression behind either failure.

**Why it matters:** The whole value of an unattended gate is that its verdict can be trusted without a human re-deriving it. A threshold that fires on machine load spends the operator's scarcest resource — attention they do not have (see [[I need the tree's output to be actionable by compute alone, because my hours don't exist]]) — and it trains the reader to discount red. The second occurrence is what makes this an opportunity rather than a one-off: the twentieth pass's own filing named a repeat as the thing worth a human's eye rather than routine re-filing.

**Distinct from its neighbours:** [[My tests carry thresholds nobody ever fixed, so nothing can come out a failure]] is the absence of a committed threshold, so nothing can come out red. This is the opposite failure — a threshold that is committed but not robust, so red carries no information. [[A failed pass reports success, so my automation can't tell]] is a false pass; this is a false fail.

**Litmus test:** More than one way to address it — express the budget as margin relative to a same-run baseline rather than absolute wall-clock; assert on work units (calls, file reads) instead of time; retry-and-confirm before reporting red; record machine load alongside the verdict so a reader can attribute it; isolate timing-sensitive tests from the contended suite; quarantine the assertion into a separate advisory lane. Real trade-offs between them. Passes.

**Evidence rung:** `assertion` — the source is the agent's own friction filing. No external party involved; floor rung per the ladder's rule.
