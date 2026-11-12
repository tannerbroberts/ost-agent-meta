---
type: Solution
status: unvalidated
created: '2026-08-02'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[Work done while a check is pending survives that check failing]]

Treat an outstanding check as a background fact rather than a barrier. The pass identifies what does not depend on the pending result — reading, mapping, annotating, drafting the next change — and does that while the check runs, collecting the verdict when it arrives.

**Compared with the alternatives:** this is the only candidate that converts waiting time into output rather than merely making it cheaper, and it needs no new infrastructure. It is also the most likely to go wrong: work started before a verdict may have to be discarded when the verdict is bad, and an agent that keeps busy while a check is pending is an agent that can quietly build on a foundation that just failed. It needs a clear rule about what genuinely does not depend on the pending result, and that rule is harder to state than it sounds.

Unvalidated, agent-ideated: a candidate for comparison, not a recommendation.

## History
- 2026-08-05 unlinked "Count how much post-handoff work in past sessions would have survived a failing check" — moved under "Work done while a check is pending survives that check failing" — the belief this test measures now has a node of its own

## Issues
- 2026-11-12 2026-11-12 unattended sweep: examined for a missing instrument and deliberately left without one. The one belief beneath it, "Work done while a check is pending survives that check failing", is tested by "Count how much post-handoff work in past sessions would have survived a failing check" — a retrospective count over past sessions in which a person judges, item by item, what "would have survived". That is a measurement of history, not behaviour a spec could be red about today and green once built, so any vitest command here would be red for a reason unrelated to the question. Judged from this node's body and the test's title; the test's body was not read. What a human should do: `ost-agent lane --set` on the test (`ost_flag_humans_required` is withheld on this surface). Not a skipped step; no instrument, lane, rung or status changed.
