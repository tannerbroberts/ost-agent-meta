---
type: Assumption
created: '2026-08-18'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion

Replacing the hard reject with a warn-then-proceed trades safety for throughput: today's guard cannot silently overwrite content nobody looked at, because it refuses to. A warning that still lets the write through assumes the operator prefers fewer stalled turns over that hard guarantee — which is a preference nobody has actually stated, and is the opposite of caution if the assumption is wrong.
