---
type: AssumptionTest
source: 'TRANSCRIPT:0f28d01f-35fa-49f0-b085-89170e306ef8'
created: '2026-08-18'
evidence: assertion
lane: humans-required
---
#AssumptionTest #unvalidated #evidence/assertion

Threshold: the operator's own read on whether the refusals in TRANSCRIPT:0f28d01f-35fa-49f0-b085-89170e306ef8 and TRANSCRIPT:0095203e-ab42-4179-a53e-a2d4d6dd6032 reflect a genuine information gap (worth documenting) or composing-under-pressure (which documentation would not fix). No exit code distinguishes those two causes from the transcript alone; it needs a person's judgment of what the agent would plausibly have done differently.

A person outside the building is the measurement here: Distinguishing an information gap from composing-under-pressure from two transcripts is a judgment call, not something an exit code can settle.

## Pre-committed threshold

**Pre-committed threshold:** the operator classifies each of the 2 transcripts as either an information gap or composing-under-pressure, and names what they would expect to have been written differently. Supported requires exactly 2 information-gap verdicts; 1 or more composing-under-pressure verdicts refutes documentation as the fix, because the sessions would have composed the same command with the constraints in front of them. "Some of both" is a real outcome and is recorded as inconclusive rather than forced either way.

This paragraph adds no new question. It restates the bar the node's own first sentence already carries, in the bold pre-commitment form `askedOf` (`src/eval/coverage.ts`) reads — this node has no `threshold:` frontmatter field, so the prose scan classifies it, and a bare `Threshold:` line matches no lead-in and reads as `absent`. Fixing that is a formatting repair, not a change to what is being asked.

The decision rule is stated in advance because the two causes point at opposite repairs and the transcripts do not distinguish them: an information gap argues for putting Monitor's constraints where a composing session sees them, and composing-under-pressure argues that no document would have been read.

What clearing this bar does not settle: whether the constraints, if documented, would be read at the moment of composing. That needs a later observation, not this operator's recollection.

_Added by the 2026-08-22 unattended sweep. Correctly humans-required — no exit code separates these two causes. No lane changed, no result recorded, no instrument set._
