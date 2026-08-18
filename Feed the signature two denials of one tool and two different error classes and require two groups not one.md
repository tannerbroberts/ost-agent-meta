---
type: AssumptionTest
source: 'TRANSCRIPT:3b9eaea5-d098-4f47-ad0a-65871012d639'
created: '2026-08-10'
evidence: assertion
threshold: >-
  Two sessions denied the same tool produce one record carrying a count of two
  and both session ids; a permission denial and an InputValidationError on the
  same tool produce two records, never one.
instrument: npx vitest run test/adapters/transcript-rollup.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.** The adapter and a fixture stream; no person is the measurement.

**What the spec asserts.** The two halves of the signature, one in each direction:
1. **It groups.** Two sessions, each denied `mcp__ost-agent__ost_check`, produce one evidence record whose body carries the count and both session ids. The ids are part of the assertion, not decoration — a roll-up that discards which sessions it covers has thrown away the only route back to the raw material.
2. **It separates.** A permission denial on `Glob` and an `InputValidationError` on `Glob` produce two records. This is the assertion that fails a too-coarse signature, and the case is taken from a real session rather than invented: `TRANSCRIPT:3b9eaea5-d098-4f47-ad0a-65871012d639` contains both, and they are a grant that was never given and a product defect respectively. An operator would not call them one event.

**Why it is red today, stated precisely.** `test/adapters/transcript-rollup.test.ts` does not exist and `adapters/transcript.ts` mints one record per session with no signature function to import, so the run is **`no-spec`** — no build permit, red for the reason every unwritten spec is red. It becomes meaningful once written against today's adapter, which cannot satisfy assertion 1 at all.

**What a green here does not settle.** Whether the grouping is *right* in the cases nobody thought to pin. The spec fixes two — one group that must merge, one pair that must not — and a signature can pass both while collapsing a third distinction an operator cares about; that judgement is a person's reading of the rolled-up corpus. It also does nothing for the eighty-five records already stored under the old scheme, and says nothing about the window boundary, where an event straddling two windows appears twice with two partial counts.

⚠️ Unvalidated. Agent-proposed; not run.

## Instrument Log
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-14 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-14 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-14 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-14 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-14 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-14 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-14 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-18 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-18 **no-spec** (exit none) `npx vitest run test/adapters/transcript-rollup.test.ts` — test/adapters/transcript-rollup.test.ts does not exist — no spec was collected, so nothing was measured
