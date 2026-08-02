---
type: Solution
status: unvalidated
created: '2026-08-02'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Resume three handed-off passes from their recorded state and check they continue correctly]]

Stop treating the wait as part of the pass. When the loop reaches a point where it can only wait, it records where it got to and exits; the check's completion is what starts the next pass, which picks up from the recorded state.

**Compared with the alternatives:** this is the only candidate where waiting costs nothing at all, because nothing is running during it. It also fits the failure the tree already knows about — a run that dies mid-wait currently loses everything after the handoff. Its cost is that the loop now needs durable state between passes and something to deliver the wake, which is real infrastructure; and it converts one long session into several, so anything the agent was holding in its head has to be written down. That last consequence may be a benefit disguised as a cost.

Unvalidated, agent-ideated: a candidate for comparison, not a recommendation.
