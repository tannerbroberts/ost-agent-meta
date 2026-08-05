---
type: AssumptionTest
source: 'agent:ideation-2026-08-03'
created: '2026-08-03'
evidence: assertion
threshold: >-
  At least 7 of the 10 most recent recorded failures are fully explained by
  working directory, resolved argv, tool versions and git SHA alone.
instrument: npx vitest run test/telemetry/failure-context-coverage.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: feasibility.** The assumption is that the context which explains a failure is knowable at the moment it fails. If most failures are explained by state that is already gone by the time the recorder runs, the snapshot is expensive decoration.

**The test.** Take the ten most recent recorded failures. For each, work out by hand what actually explained it, then ask whether the four proposed fields would have carried that explanation. Score each as explained, partly explained, or not explained. The founding case for this opportunity — a build step run from the home directory instead of the repo — is explained by `cwd` alone and should be counted, but it should not be the only one that is.

**Why this is small and fast.** It needs no build at all. The records already exist; the work is reading ten of them and being honest about what each needed. An afternoon.

**Why the threshold is where it is.** Below 7 of 10 the field set is not carrying the class, and the right response is to widen the fields or prefer "Replay a recorded failure in its recorded context on demand", which does not need to predict what will matter. A result between 7 and 9 argues for shipping this as the floor and escalating to replay only for the remainder.

**What a result here does not settle.** It says nothing about whether operators would *trust* an enriched record enough to stop re-running by hand — that is the desirability question, and it belongs to a different test.

Proposed, not run. Recording a result is a human's `ost-agent result`.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/telemetry/failure-context-coverage.test.ts — The threshold — at least 7 of the 10 most recent recorded failures fully explained by working directory, resolved argv, tool versions and git SHA alone — is scored against committed material: the spec carries the ten failures with what actually explained each, asks whether the four snapshot fields would have carried that explanation, and asserts at least seven come back fully explained. It fails today because nothing captures the four fields at failure time and no labelled failure set is committed to score against.

## Instrument Log
- 2026-08-04 **red** (exit 1) `npx vitest run test/telemetry/failure-context-coverage.test.ts` — filter:  test/telemetry/failure-context-coverage.test.ts
