---
type: AssumptionTest
source: >-
  INBOX:friction/2026-08-10-friction-pr-80-shipped-a-pass-claims-the-work-item-before.md
created: '2026-08-10'
evidence: assertion
threshold: >-
  The guard refuses a `shipped` node carrying no witness, accepts one whose
  witness resolves, and refuses one whose witness names a path absent from the
  repository. All three, or the run fails.
instrument: npx vitest run test/ost/shipped-requires-witness.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.** Three fixture nodes and a resolver; nobody is the measurement.

**What the spec asserts.** Over a fixture vault:
1. Setting `status: shipped` on a solution with no `witness:` field is refused.
2. A node whose witness names a line that exists in the repository is accepted.
3. A node whose witness names a path the repository does not contain is refused — this is the assertion that separates a resolver from a required text field, and the one an implementation is most likely to skip.

**Why it is red today, stated precisely.** `test/ost/shipped-requires-witness.test.ts` does not exist and there is no witness field for it to exercise, so the run is **`no-spec`**: red for a reason common to every unwritten question, no build permit. It becomes red-about-something once the spec is written against `ost_set_status` as it stands, which accepts `shipped` unconditionally.

**What a green here does not settle, and it is most of the assumption.** The belief this test sits under is about the *existing corpus* — whether the nodes already marked shipped can each name a witness, or whether the rule would demote working mechanisms. A spec over fixtures cannot answer that: it proves the guard behaves, not that the tree survives it. Five nodes in the current `solutionsMissingInstruments` bucket carry `shipped`, and at least two of them describe diffuse behaviour — a refusal inside a write boundary, a redaction inside a funnel — with no single reaching line to name. Somebody has to run the resolver over the real vault and count, and that census is not this test.

It also settles nothing about whether a stricter `shipped` is wanted, which is a preference and would need people.

⚠️ Unvalidated. Agent-proposed; not run.

## Instrument Log
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/ost/shipped-requires-witness.test.ts` — test/ost/shipped-requires-witness.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/ost/shipped-requires-witness.test.ts` — test/ost/shipped-requires-witness.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/ost/shipped-requires-witness.test.ts` — test/ost/shipped-requires-witness.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/ost/shipped-requires-witness.test.ts` — test/ost/shipped-requires-witness.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/ost/shipped-requires-witness.test.ts` — test/ost/shipped-requires-witness.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/ost/shipped-requires-witness.test.ts` — test/ost/shipped-requires-witness.test.ts does not exist — no spec was collected, so nothing was measured
