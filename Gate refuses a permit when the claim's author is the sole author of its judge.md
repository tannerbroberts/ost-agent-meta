---
type: AssumptionTest
source: 'INBOX:2026-08-10-founder-doctrine-machine-witness-parity.md'
created: '2026-08-11'
evidence: assertion
threshold: >-
  Gate returns BLOCKED with a separation reason on the same-author fixture and
  does not block on separation grounds on the distinct-author fixture.
instrument: npx vitest run test/eval/author-judge-separation.test.ts
---
#AssumptionTest #machine-witness #goal-acquisition #unvalidated #evidence/assertion

One small, fast test of one belief: that author–judge separation can be read off the vault's own records and enforced at gate time.

**Design.** Two fixture vaults. In the first, one actor authors the solution, its assumption test, and the recorded verdict — same provenance throughout. In the second, the claim and its judge carry distinct recorded authors. Run the gate against both.

**What the spec asserts.** `test/eval/author-judge-separation.test.ts` asserts the gate returns BLOCKED on the same-author fixture with a reason naming the separation rule, and CLEARED (or blocked only for other, stated reasons) on the distinct-author fixture. It is red today because no separation rule exists in the gate and the spec has not been written — a `no-spec` red, which grants nothing; the deliverable is the failing spec, and this test is unfinished until the spec exists and fails on an assertion.

**What a green would NOT settle.** A passing check proves the record distinguishes authors and the gate reads it. It does not prove the separation is real independence — one actor split across two sessions satisfies the record while remaining one author, which is the third failure mode the parent assumption names and which this spec cannot reach. That residue belongs to the dissent-panel measurement, not to this test.

## Instrument Log
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-14 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-14 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-14 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-14 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-14 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-14 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-14 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/eval/author-judge-separation.test.ts` — test/eval/author-judge-separation.test.ts does not exist — no spec was collected, so nothing was measured
