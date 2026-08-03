---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: At least 2 of 3 judges name the same assumption on at least 6 of 10 solutions.
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that an independent judge produces something better grounded than the author's own view. If the judge is another model with no independent grounding, it may generate plausible nominations with no more basis — and the appearance of corroboration is more dangerous than an openly self-assessed gate.

**Risk category: feasibility.**

**Design.** Take ten solutions. Have three judges — ideally not all of the same kind — each independently name the riskiest assumption, seeing only the solution. Measure agreement among the three. Judges who agree with each other are at least reading something real; three judges scattering across ten different nominations are generating, not judging.

**Why it is small.** Ten solutions from the tree, three passes over each, and a comparison.

**What it will not cover.** Agreement is not correctness. Three judges could converge on the same wrong assumption, particularly if they share training or read the same framing in the solution's own text.

A human runs this and records the result.
