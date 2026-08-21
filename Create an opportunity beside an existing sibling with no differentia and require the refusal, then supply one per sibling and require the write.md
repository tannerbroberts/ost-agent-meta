---
type: AssumptionTest
source: 'agent-ideated:2026-08-20-unattended-sweep'
created: '2026-08-20'
evidence: assertion
threshold: >-
  4 of 4 cases pass on a fixture vault whose parent Opportunity already holds 2
  Opportunity children: (1) a 3rd child created with 0 differentia sentences is
  refused and 0 files are written; (2) a 3rd child with 1 sentence for 2
  siblings is refused and the refusal names the 1 sibling left unaddressed; (3)
  a 3rd child with 2 sentences, 1 per sibling, is written with both sentences in
  its body; (4) a 1st child under a parent with 0 Opportunity siblings is
  written with 0 sentences required. 3 of 4 or fewer refutes the gate as
  described.
instrument: npx vitest run test/ost/sibling-differentia-guard.test.ts
sight: grounded
---
#AssumptionTest #unvalidated #evidence/assertion

**Kind: feasibility.** Whether the gate the solution describes can be built as a pure create-time check — sibling set computed from the parent's existing Opportunity children, one sentence required per sibling, refusal before any write — without the tool reading the sentence for quality.

**Lane: compute-only.**

**What the spec asserts.** Against the same fixture-vault helper `test/ost/` already uses (`fixture-vault.ts`): four cases — no-siblings create passes unchanged; siblings present and no differentia → refused, nothing on disk; siblings present and a differentia for one of two → refused, the message names the missing sibling; a differentia per sibling → written, and the sentences are in the body. The refusal-before-write assertion matters most, because `ost_create_node`'s contract is that a refused call leaves no file.

**Why it is red today, and which kind of red.** Read against the repository this pass: the `ost_create_node` schema has no differentia argument, and the hierarchy check inspects the parent's layer only, never the parent's other children. The spec file does not exist either, so this is a **no-spec red** — the mechanism is named (the create path in `src/ost/` that `ost_create_node` calls, and the tool schema in `src/mcp/server.ts`), the assertions are stated, and the builder's deliverable is the guard and the spec together, not a file.

**What a green does not settle.** Whether the sentences authors write under the gate discriminate anything. A gate can require a sentence and cannot judge one; that is "The operator grades the first ten differentia statements as discriminators or filler" under the sibling assumption, which needs a person. A green here plus a high filler rate there is the case the solution's own prose calls worse than no gate.

## Instrument Log
- 2026-08-20 **no-spec** (exit none) `npx vitest run test/ost/sibling-differentia-guard.test.ts` — test/ost/sibling-differentia-guard.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-20 **no-spec** (exit none) `npx vitest run test/ost/sibling-differentia-guard.test.ts` — test/ost/sibling-differentia-guard.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-20 **no-spec** (exit none) `npx vitest run test/ost/sibling-differentia-guard.test.ts` — test/ost/sibling-differentia-guard.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-20 **no-spec** (exit none) `npx vitest run test/ost/sibling-differentia-guard.test.ts` — test/ost/sibling-differentia-guard.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-21 **no-spec** (exit none) `npx vitest run test/ost/sibling-differentia-guard.test.ts` — test/ost/sibling-differentia-guard.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-21 **no-spec** (exit none) `npx vitest run test/ost/sibling-differentia-guard.test.ts` — test/ost/sibling-differentia-guard.test.ts does not exist — no spec was collected, so nothing was measured
