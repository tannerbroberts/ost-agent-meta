---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

No coordination up front. Every write carries a fingerprint of the state it was composed against, and the write is refused if that state has changed. The refusal names what moved and who moved it. Agents proceed optimistically and are stopped only where they would actually collide.

This suits an append-only vault well, because the genuine collisions are rare and narrow — two appends to different nodes are not a collision at all, however concurrent they are.

**Compared to the alternatives.** Costs nothing when there is no contention, which is nearly always, and it never serialises work that did not need serialising. It also never prevents the wasted effort: an agent that composed a whole pass against stale state finds out at the end, and has to redo it. A lock would have made it wait first; branches would have let it finish and merge.

**What would make this the wrong pick.** Detection catches the write and not the reasoning. An agent that read the tree, formed a plan, and had its premise invalidated will have most of its writes accepted and one refused, leaving a partially-applied plan built on something no longer true — which is a worse state than either colliding cleanly or waiting.
