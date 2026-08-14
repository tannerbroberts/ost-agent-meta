---
type: AssumptionTest
source: 'TRANSCRIPT:3b9eaea5-d098-4f47-ad0a-65871012d639'
created: '2026-08-10'
evidence: assertion
threshold: >-
  Three ids cited by one node all leave the unmapped list; a legacy
  single-string node still maps; and a node citing one `stated` source alongside
  two `assertion` sources is capped at `assertion`.
instrument: npx vitest run test/ost/multi-source-mapping.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.** A fixture vault and a derivation; no person is the measurement.

**What the spec asserts.** Three things, and the third is the one worth writing the spec for:
1. A node citing three stored evidence ids removes all three from `unmappedEvidence`.
2. A node whose `source` is a plain string behaves exactly as it does today. Written second because it is the regression that would be discovered in production otherwise.
3. A node citing one `stated`-earning source and two `assertion`-earning sources is capped at `assertion` — the weakest, not the strongest.

That third assertion is where the assumption is genuinely at risk. A list gives the rung ceiling a question it has never had to answer, and taking the strongest source in the list is both the intuitive implementation and a free promotion for any node willing to cite one good source alongside forty weak ones. Pinning the weakest here is a pre-commitment, made before the code exists, so nobody chooses the rule after seeing which nodes it demotes.

**Why it is red today, stated precisely.** `test/ost/multi-source-mapping.test.ts` does not exist and `source` is a single string, so the run is **`no-spec`** — the weak red, indistinguishable from every other unwritten question. Once the spec exists it goes red against today's derivation in `src/processes/tree.ts`, which compares one string.

**What a green here does not settle.** Whether the citations are honest. Nothing in an exit code distinguishes forty ids a pass distilled from forty it skimmed, and the solution node names that as its central risk. It also says nothing about `classifyProvenance`'s handling of the non-evidence prefixes `WEB:` and `INTERVIEW:` appearing in a mixed list, which needs its own assertion and is not in this threshold.

⚠️ Unvalidated. Agent-proposed; not run.

## Instrument Log
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-14 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-14 **no-spec** (exit none) `npx vitest run test/ost/multi-source-mapping.test.ts` — test/ost/multi-source-mapping.test.ts does not exist — no spec was collected, so nothing was measured
