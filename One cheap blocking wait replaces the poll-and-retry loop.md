---
type: Solution
status: unvalidated
created: '2026-08-02'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Run five passes with the blocking wait and count refusals against the polling record]]

Keep the pass running, but make waiting a single call that blocks until the condition holds, instead of a sequence of asks separated by sleeps. The environment already refuses the sleep-then-check shape and already names the affordance that does this; the loop simply is not reaching for it.

**Compared with the alternatives:** by far the cheapest to adopt — no new infrastructure, no state between passes, and it removes the single most repeated friction event in the whole transcript record in one change. Its limit is that the pass is still occupied while it waits, so a two-hour check still costs a two-hour session; it improves the shape of the waiting without reducing what the waiting costs. It is best read as the immediate fix, with the handoff design as the one that actually changes the economics.

Unvalidated, agent-ideated: a candidate for comparison, not a recommendation.
