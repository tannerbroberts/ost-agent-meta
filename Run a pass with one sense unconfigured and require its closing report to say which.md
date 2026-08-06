---
type: AssumptionTest
source: 'agent-run:autonomous-loop-2026-08-06'
created: '2026-08-06'
evidence: assertion
threshold: >-
  The closing report lists every sense with a state, including senses nothing
  reached for during the run. A sense that was never tried must be
  distinguishable from one that worked — if the two render identically, this is
  refuted.
instrument: npx vitest run test/loop/sense-census-report.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.** Run a pass against a fixture with `product.repos` unconfigured and the web budget spent, and assert the closing report enumerates every sense with a state — derived from config and grant, not from what the pass happened to touch.

**Why it is red today, on the mechanism.** No pass emits a sense census. `ost_ingest_inbox` emits the analogous thing for write-channels — six lines including "[atlassian] disabled — turned off in ost.config.yaml" — and that report is derived from config with nothing having been tried, which is the precedent this borrows. Nothing equivalent exists for the senses a pass reads *with*, which is why the 2026-08-06 sweep's own summary could not distinguish a sense it never used from one that worked.

**The half of the threshold most likely to fail, stated in advance so a red there counts.** "A sense nothing reached for is distinguishable from one that worked" is the demanding clause. If the census can only be assembled from observed denials, then a sense nothing tried renders as fine, and the mechanism has reproduced the exact ambiguity it was built to remove. That is a refutation of the assumption, not a bug in the test.

**What a green run does not settle.** It proves the report can be produced. It says nothing about whether anyone reads it — and this loop's standing problem is that its output already exceeds what gets reviewed, so a census nobody opens changes nothing about the degraded work that still went into the tree. Desirability and usability are both untouched.

## Instrument Log
- 2026-08-06 **red** (exit 1) `npx vitest run test/loop/sense-census-report.test.ts` — No test files found, exiting with code 1
