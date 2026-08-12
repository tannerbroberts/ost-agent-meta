---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  0 acknowledgements are judged avoidance, and at most 2 in 10 are judged
  arguable.
instrument: npx vitest run test/ost/acknowledge-evidence.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that acknowledgement is used honestly. A pass that can dismiss its own backlog will eventually dismiss something that mattered, and the reason it writes will sound entirely reasonable — which is what makes this the most dangerous verb on the surface.

**Risk category: feasibility, with a real governance dimension.**

**Design.** Let one pass acknowledge items it judges unactionable, with reasons, on the eighteen currently stranded and anything else it reaches for. Then a human reads every acknowledgement against the item and sorts each into correct, arguable, or avoidance. The avoidance count is the finding, and every instance is a specification for a restriction.

**Why it is small.** One pass and one review sitting, against a backlog that already exists.

**What it will not cover.** A pass acknowledging while it knows the acknowledgements will be reviewed is on its best behaviour. The honest version of this measures a pass that expects no audit, and there is no clean way to arrange that.

Who may acknowledge, and whether it expires, are human decisions. A human runs this and records the result.

## History
- 2026-08-05 instrument: (none) → npx vitest run test/ost/acknowledge-evidence.test.ts — Asserts the verb the surface lacks: an acknowledged item leaves unmappedEvidence without being deleted or mapped, its reason persists append-only, and "corroborates [[X]]" is stored as a distinct verdict from "no genuine need" so only the first can strengthen a node later. Red today because no acknowledge verb exists and mapping is carried solely by node source frontmatter.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/ost/acknowledge-evidence.test.ts` — No test files found, exiting with code 1
- 2026-08-12 **green** (exit 0) `npx vitest run test/ost/acknowledge-evidence.test.ts` — ✓ "corroborates [[X]]" is a distinct verdict from "no genuine need" > a hand-mangled verdict fails closed in both directions: no work removed, no node strengthened 344ms
