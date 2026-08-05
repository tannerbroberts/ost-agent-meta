---
type: AssumptionTest
source: 'TRANSCRIPT:e335a680-ee48-4171-b8ad-4cfb526e4129'
created: '2026-08-04'
evidence: assertion
threshold: >-
  Built against the repository state of the failing session, the index reports
  `reconcileWithUsage` absent, `reconcileWithGit` present, and `configProblem`
  absent from `ToolContext` — all three, no misses.
instrument: npx vitest run test/runner/symbol-index.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Category: feasibility.** The assumption is that the project's symbol surface can be extracted mechanically and is accurate enough to have prevented the two captured failures. If the index cannot answer the exact three questions the compiler already answered, the manifest is not worth putting in front of a run.

**Lane: compute-only.** No person is the measurement here — the answer is an exit code from a spec file over committed source.

**Why this bar and not a broader one.** The three lookups are taken verbatim from `TRANSCRIPT:e335a680-…`, so passing means the index would have caught what actually went wrong rather than what might. A softer bar — "the index finds most exports" — would pass on an index that missed type members, and `configProblem` is a type member, which is the harder half.

**What a green run does NOT settle.** It says the index can be built and is correct on three known cases. It says nothing about whether a run given the index would consult it, nothing about whether the index is small enough to be worth the context it costs, and nothing about whether anyone other than this project wants the feature. Desirability, viability and usability are exactly where they were before the command ran.

## Definition of done

`npx vitest run test/runner/symbol-index.test.ts`

Red today: `test/runner/symbol-index.test.ts` does not exist, and neither does the index it would exercise.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/runner/symbol-index.test.ts` — No test files found, exiting with code 1
