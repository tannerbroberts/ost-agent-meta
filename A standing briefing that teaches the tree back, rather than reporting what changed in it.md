---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Have the operator answer questions about their own tree from the briefing alone]]

The agent keeps a short standing document whose job is comprehension rather than record: where the tree currently stands, which branch is live and why, what the last week's evidence changed about the picture, and which belief the whole thing is currently resting on. It is rewritten in full each pass, and it is written to be read cold by someone who has not been following.

The distinction from a changelog is the whole idea. A list of what changed requires the reader to already hold the tree in their head; a briefing rebuilds the tree in their head each time, which is the thing tending it used to do.

**Compared to the alternatives.** Costs the operator minutes rather than hours, so it is the only option that survives contact with a busy week — and understanding maintained badly every week beats understanding maintained perfectly until the operator stops. It also carries the least guarantee: reading a summary is not deciding, and the operator ends up holding the agent's picture of the tree rather than their own.

**What would make this the wrong pick.** The briefing is written by the same agent whose judgement it is meant to keep the operator able to check. If the agent has misread the tree, the briefing will misread it identically and confidently, and the operator has no independent view left to catch it with.

## Definition of done

[[Have the operator answer questions about their own tree from the briefing alone]]

`npx vitest run test/ost/standing-briefing.test.ts`

The spec asserts the briefing is regenerated in full each pass and names the belief the tree is currently resting on — the weakest rung of the believability rollup, which the tree already computes. That is the mechanical core of "rebuilds the tree in the reader's head" rather than "lists what changed". Red today because no standing briefing is generated.

**What a green here does not settle, and it is the node's own objection.** The briefing is written by the same agent whose judgement it is meant to keep the operator able to check. If the agent has misread the tree, a full regeneration will misread it identically and confidently, and a passing spec will confirm only that the misreading was complete and freshly dated. Whether an operator can actually answer questions about their own tree from it is the humans-required test, and it is the one that matters here.
