---
type: Opportunity
status: unvalidated
source: 'TRANSCRIPT:5bbed804-1d15-44bd-8751-e1c0a87aed12'
created: '2026-08-02'
evidence: observed
---
#Opportunity #unvalidated #evidence/observed

Across at least six separate captured sessions the agent reached for the same shape — wait a while, then check on something — by writing `sleep 45` followed by a status command. Every time, the call was refused with the same message pointing at the right affordance. Every time, the agent adapted within the session. Every time, the next session started over and made the identical call.

The cost is small per instance and unbounded in aggregate: it is paid once per session, forever, and it never appears as a failure because the session recovers. What is missing is not a better error message — the message is already clear and already names the alternative. What is missing is any path by which a lesson learned at 14:00 on Tuesday is still known at 09:00 on Wednesday.

**The need:** I want what the agent worked out the hard way last session to still be known the next time it starts.

More than one way to address this: promote the recurring refusals into standing guidance the agent reads at startup, let a session write a durable note to itself that survives context, detect a repeat-offender pattern across sessions and surface it as a rule to adopt, or fix the affordance so the natural form is the working one.

## Provenance

Distilled from `TRANSCRIPT:5bbed804-1d15-44bd-8751-e1c0a87aed12`, a two-event session whose entire friction content is one shell-quoting error and one blocked sleep-then-poll.

Corroborated by the same blocked pattern in sessions `0d27cebf` (twice), `470cb94a` (twice), `4ff7b605`, `516fdfb8` and `5960b7ec` — seven or more instances of one refusal across seven days, none of which changed the next session's first instinct.

## Issues
- 2026-08-02 Possible gate conflict — flagged by the pass that created it, 2026-08-02. This node's parent "What the agent learns doesn't accumulate over time" is placed by the human-authorized prioritization of 2026-07-24 in the founder-theory lane, marked evidence-debt-gated: "no new siblings until a non-founder artifact cites the row." Whether this node clears that gate turns on a question the pass could not answer for itself — this node rests on `TRANSCRIPT:5bbed804` and twelve corroborating sessions, which is machine-captured rather than founder-authored, but it is still the product's own agent rather than an outside party. If "non-founder artifact" means anything not originating inside this building, the gate is not cleared and this node should wait. If it means evidence not composed by a person's assertion, it is cleared and this is the first row in that lane to have earned growth. A human's call, and the answer applies to every future node in the lane.
