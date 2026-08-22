---
type: AssumptionTest
source: 'TRANSCRIPT:0f28d01f-35fa-49f0-b085-89170e306ef8'
created: '2026-08-18'
evidence: assertion
lane: humans-required
---
#AssumptionTest #unvalidated #evidence/assertion

Threshold: a clear yes/no from someone who can read Monitor's own implementation (the harness maintainer), on whether a structured wait-for-condition primitive is separable from the general command_substitution refusal. Neither the OST-Agent repository nor this vault's tooling contains Monitor's implementation, so no spec file in either can settle this.

A person outside the building is the measurement here: The harness maintainer is irreducibly the measurement — Monitor's refusal logic lives in Claude Code's own tool implementation, outside both the OST-Agent repository and this vault, so no command this tree can run observes it.

## Pre-committed threshold

**Pre-committed threshold:** a yes or no from the harness maintainer, with at least 1 pointer into Monitor's own implementation naming where the refusal is enforced. A yes counts as support only if it also states whether the primitive would carry a maximum wait; a yes with no bound is a different proposal and scores inconclusive. "Probably" or "shouldn't be hard" is inconclusive, not support.

This paragraph adds no new question. It restates the bar the node's own first sentence already carries, in the bold pre-commitment form `askedOf` (`src/eval/coverage.ts`) reads — this node has no `threshold:` frontmatter field, so the prose scan classifies it, and a bare `Threshold:` line matches no lead-in and reads as `absent`.

The pointer-into-the-implementation clause is what keeps this answerable rather than speculative: the node's own second paragraph records that Monitor's refusal logic lives in Claude Code's tool implementation, outside both the OST-Agent repository and this vault, so nobody here can check an answer given without one.

What clearing this bar does not settle: whether the harness maintainers would prioritize building it. Separability and willingness are different questions and only the first is asked here.

_Added by the 2026-08-22 unattended sweep. Correctly humans-required — the implementation is outside every repository this tree can read. No lane changed, no result recorded, no instrument set._
