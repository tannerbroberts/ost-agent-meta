---
type: AssumptionTest
source: 'TRANSCRIPT:3b9eaea5-d098-4f47-ad0a-65871012d639'
created: '2026-08-10'
evidence: assertion
threshold: >-
  A `--matching` disposition withholds a record captured AFTER it was written,
  `ost_next_work` reports the live match count rather than withholding silently,
  and the two `friction/` records — which carry distinct content — are not
  matched by the transcript pattern.
instrument: npx vitest run test/knowledge/disposition-pattern.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.** A matcher over a fixture corpus; no person is the measurement.

**What the spec asserts.** Build a fixture corpus in the shape of the real one — transcript records whose only content is a tool denial, plus two content-bearing `friction/` records — and then:
1. A pattern dismissal withholds a matching record that is captured *after* the dismissal was recorded. This is the live-predicate property and it is the whole difference between this and a batch loop.
2. The two content-bearing records are not withheld. This is the false-positive assertion and the one that should be hardest to pass.
3. `ost_next_work` reports how many records the pattern is currently withholding. A standing dismissal that hides silently is the failure mode the solution node names as its real price, so the count is part of the definition of done rather than a nicety.

**Why it is red today, stated precisely.** `test/knowledge/disposition-pattern.test.ts` does not exist and `dispose` takes no `--matching` argument, so the run is filed **`no-spec`** and mints no build permit. That is the weak red: it fails for a reason every unwritten question shares. It becomes red-about-something once the spec is written against today's `src/knowledge/dispositions.ts`, where a disposition subject is a single id.

**What a green here does not settle, and it is the larger half.** The coverage ratio over the *real* eighty-five records — the number the assumption is actually about. A fixture proves the matcher behaves; it cannot tell anyone whether a pattern an operator would willingly write covers seventy of the queue or twenty of it. That is a census over the stored corpus and somebody has to run it. Nor does it touch whether an operator wants a standing dismissal at all, which is a preference and would need people.

⚠️ Unvalidated. Agent-proposed; not run.

## Instrument Log
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-14 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-14 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-14 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-14 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-14 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-14 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-14 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-18 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-18 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-18 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-18 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-18 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-18 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-18 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-18 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-18 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-18 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-18 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-18 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-18 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-18 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-18 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-18 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-18 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-18 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-18 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-18 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-18 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-19 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-19 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-19 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-19 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-19 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-19 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-19 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-19 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-19 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-19 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-19 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-19 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-20 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-20 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-20 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-20 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-20 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-20 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-20 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-20 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-20 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-20 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-20 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-20 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-20 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-20 **no-spec** (exit none) `npx vitest run test/knowledge/disposition-pattern.test.ts` — test/knowledge/disposition-pattern.test.ts does not exist — no spec was collected, so nothing was measured
