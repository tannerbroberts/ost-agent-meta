---
type: Opportunity
source: 'TRANSCRIPT:081b644b-e90a-472e-9b3d-15562a030a94'
created: '2026-08-06'
evidence: observed
---
#Opportunity #unvalidated #evidence/observed

Observed in two separate sessions: `sleep 45 && gh pr checks 54`, `sleep 30 && gh pr checks 55`, `sleep 45 && gh pr checks 17` — each blocked with the same guidance about `until`-loops and background runs, each rediscovered from scratch. The same sessions carry three identical `TaskOutput` re-polls of the same task id, which is the same need expressed through a channel that does not refuse it.

The need is not for the guard to be removed — the refusal is correct. It is that waiting for something slow is a routine, recurring act with no first-class way to express it, so the operator's agent pays the discovery cost again in every session that has to wait for CI.

## Issues
- 2026-08-06 Probable duplicate of "My loop spends its time waiting for a check it cannot subscribe to" — flagged, not merged, and the reason for not merging is structural rather than squeamish.

**Why they look like one claim.** This node's stated need is that "waiting for something slow is a routine, recurring act with no first-class way to express it." That other node's need is "I want to be told when the check finishes, rather than pay to keep asking whether it has," and one of the four directions it names is "hand the wait to something built to block cheaply" — which is this node's need in that node's own words. It already carries three solutions covering the space: "The pass ends at the handoff, and the finished check wakes the next one", "One cheap blocking wait replaces the poll-and-retry loop", and "Take up independent work while a check is outstanding". Any candidate ideated under this node would land on top of one of those three.

The evidence overlaps too. This node cites `TRANSCRIPT:081b644b` and the `sleep 45 && gh pr checks 54/55/17` shape; the other node's corroboration sections cite the same construct across twelve sessions and eleven distinct pull requests, including `516fdfb8`, which both nodes rest on.

**Why they might be two claims.** This node sits under "The same refusal is rediscovered every session, because nothing carries the lesson forward", and its distinguishing content is the *rediscovery* cost — paying to relearn the refusal in every new session — rather than the cost of polling itself. That is a real and separate expense. The difficulty is that the rediscovery cost is exactly what its parent already holds, which leaves this node holding the intersection of two needs the tree carries separately.

**What would settle it:** whether a first-class wait affordance would end the rediscovery. If a permitted way to wait exists and the agent still reaches for `sleep` next session, the rediscovery need is genuinely separate and this node should stay and grow its own candidates. If shipping the affordance ends both complaints at once, these are one claim and this node should be folded into the other.

**Why this pass did not merge them.** The two sit under different parents, so folding this one into the other would repoint this node's inbound edge onto a node that already has a parent, leaving a survivor with two parents — a single-parent violation the tree forbids. Doing it correctly needs a detach first, and that means deciding which of the two parents the merged need belongs under. That placement was chosen deliberately by the 2026-08-06 pass that created this node, one day ago, and overturning it with a call that deletes a file is past what an unattended sweep should decide on ~75% confidence.

**If it were mine to call:** detach this node from "The same refusal is rediscovered every session", merge it into "My loop spends its time waiting for a check it cannot subscribe to", and carry this node's sharper framing — that the refusal is correct and the missing thing is an expressible wait — into the survivor's prose, because that sentence is better than anything in the survivor today.
