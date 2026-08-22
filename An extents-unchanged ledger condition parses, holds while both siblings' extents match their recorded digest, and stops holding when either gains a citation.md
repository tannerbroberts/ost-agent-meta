---
type: AssumptionTest
source: 'agent-ideation:2026-08-21-unattended-sweep'
created: '2026-08-21'
evidence: assertion
threshold: >-
  5 of 5 assertions hold: the condition parses; conditionHolds is true on the
  seeded pair; the shared-extent flag is absent and listed under
  suppressedByCondition; after 1 new citation beneath either sibling
  conditionHolds is false and the flag returns; a condition naming a node not in
  the tree evaluates false.
instrument: npx vitest run test/ost/suppression-extent-condition.test.ts
sight: grounded
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.** The exact harness `test/ost/suppression-condition.test.ts` uses — `initVault`, `appendSuppression`, `parseSuppressionCondition`, `conditionHolds`, `computeNextWork` — extended by one condition kind. No person.

**What the spec asserts.** `parseSuppressionCondition({ holdsWhile: "extents-unchanged", nodes: [A, B], digest: <sha of both sorted extents> })` returns a typed condition rather than throwing `PROSE_REFUSAL`. On a temp vault where A and B share one record and `computeNextWork` reports `shared-extent`, `appendSuppression` with that condition removes the flag from `hygieneIssues`, lists it under `suppressedByCondition` with the right `list`, and leaves `done` true. Then create one more node citing a fresh record beneath B: `conditionHolds` flips to false with no ledger write, and the flag (now `subset-extent`) is back on the next call. Fail-open control, copied from the existing spec: a condition over a node that left the tree evaluates false.

**Why it is red today, and for a reason specific to this question.** `src/knowledge/suppressions.ts` knows four `holdsWhile` kinds — `status-is`, `lane-is`, `lane-unlabelled`, `section-missing` — and refuses anything else as prose; the very first assertion throws `PROSE_REFUSAL` against today's code. That is a red on the mechanism this solution needs. **This surface cannot write the spec file, so the command currently fails on `No test files found`, is filed `no-spec`, and grants no permit** — the deliverable is the file with the assertions above.

**What a green does NOT settle.** Whether a human ever writes the ledger entry; the write path is the CLI's by design, so desirability here is a person's willingness to run one command per verdict, which only firings over time can show.

⚠️ Proposed only — the agent does not run tests or record results.

## Instrument Log
- 2026-08-21 **no-spec** (exit none) `npx vitest run test/ost/suppression-extent-condition.test.ts` — test/ost/suppression-extent-condition.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-21 **no-spec** (exit none) `npx vitest run test/ost/suppression-extent-condition.test.ts` — test/ost/suppression-extent-condition.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-21 **no-spec** (exit none) `npx vitest run test/ost/suppression-extent-condition.test.ts` — test/ost/suppression-extent-condition.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-21 **no-spec** (exit none) `npx vitest run test/ost/suppression-extent-condition.test.ts` — test/ost/suppression-extent-condition.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-21 **no-spec** (exit none) `npx vitest run test/ost/suppression-extent-condition.test.ts` — test/ost/suppression-extent-condition.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/ost/suppression-extent-condition.test.ts` — test/ost/suppression-extent-condition.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/ost/suppression-extent-condition.test.ts` — test/ost/suppression-extent-condition.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/ost/suppression-extent-condition.test.ts` — test/ost/suppression-extent-condition.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/ost/suppression-extent-condition.test.ts` — test/ost/suppression-extent-condition.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/ost/suppression-extent-condition.test.ts` — test/ost/suppression-extent-condition.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/ost/suppression-extent-condition.test.ts` — test/ost/suppression-extent-condition.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/ost/suppression-extent-condition.test.ts` — test/ost/suppression-extent-condition.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/ost/suppression-extent-condition.test.ts` — test/ost/suppression-extent-condition.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/ost/suppression-extent-condition.test.ts` — test/ost/suppression-extent-condition.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/ost/suppression-extent-condition.test.ts` — test/ost/suppression-extent-condition.test.ts does not exist — no spec was collected, so nothing was measured
