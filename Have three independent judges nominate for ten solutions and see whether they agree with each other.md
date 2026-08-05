---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: At least 2 of 3 judges name the same assumption on at least 6 of 10 solutions.
instrument: npx vitest run test/eval/judge-panel-agreement.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that an independent judge produces something better grounded than the author's own view. If the judge is another model with no independent grounding, it may generate plausible nominations with no more basis — and the appearance of corroboration is more dangerous than an openly self-assessed gate.

**Risk category: feasibility.**

**Design.** Take ten solutions. Have three judges — ideally not all of the same kind — each independently name the riskiest assumption, seeing only the solution. Measure agreement among the three. Judges who agree with each other are at least reading something real; three judges scattering across ten different nominations are generating, not judging.

**Why it is small.** Ten solutions from the tree, three passes over each, and a comparison.

**What it will not cover.** Agreement is not correctness. Three judges could converge on the same wrong assumption, particularly if they share training or read the same framing in the solution's own text.

A human runs this and records the result.

## History
- 2026-08-05 instrument: (none) → npx vitest run test/eval/judge-panel-agreement.test.ts — The bar in this node's own threshold field is arithmetic over a fixed corpus — "At least 2 of 3 judges name the same assumption on at least 6 of 10 solutions" — and every input it needs is already committed: ten Solution nodes in this vault, each judge seeing only the solution body. The spec drives three independently-configured judges over the same ten solutions, normalises each nomination to the assumption it names, and asserts the majority-agreement count against the 6-of-10 bar, reporting the scatter (three distinct nominations on one solution) separately, because the node is explicit that scattering means the panel is generating rather than judging. It fails today because there is no judge-panel harness at all: `test/eval/riskiest-assumption-judge.test.ts` scores ONE judge against a labelled set, and nothing in the product runs several judges over one solution or compares their nominations to each other, so there is no agreement figure to assert. What it does not settle is the thing the node itself flags — agreement is not correctness, and three judges sharing training can converge on the same wrong assumption; a green here says the panel is readable, not that it is right.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/eval/judge-panel-agreement.test.ts` — No test files found, exiting with code 1
