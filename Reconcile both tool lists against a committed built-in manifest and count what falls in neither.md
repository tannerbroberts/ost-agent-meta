---
type: AssumptionTest
source: 'agent-ideation:2026-08-10-unattended-sweep'
created: '2026-08-10'
evidence: assertion
threshold: >-
  Zero built-ins fall in neither list. The count of unaccounted names must be 0;
  it is at least 3 today (Read, Glob, Grep), and the spec must name them rather
  than reporting a bare number.
instrument: npx vitest run test/release/surface-enumeration.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.** Nothing here needs a person: the two lists are committed strings in `examples/automation/autonomous-pass.sh`, and the denominator is a committed manifest. A spec settles it.

**What the spec does.** Extract `OST_TOOLS` and `DENIED_TOOLS` from `examples/automation/autonomous-pass.sh` the same way `test/release/examples-allowlist.test.ts` already extracts them — that file is the precedent for parsing the shipped script rather than a copy of it. Then load the committed manifest of host built-in names and assert the three-way accounting: every manifest entry is in the grant or the deny list, the two lists stay disjoint, and the set of unaccounted names is empty. On failure it prints the unaccounted names.

**Why it fails today, and what it does not settle.** It fails today for a reason specific to this question: `Read`, `Glob` and `Grep` are in neither list, and the 2026-08-10 sweep used all three against the vault. The spec goes green only once each of those three has been decided about — granted deliberately or denied — and the manifest exists to compare against. It says nothing about whether granting a read tool to an unattended pass is *wise*, which is a judgement, nor about capability reached through a granted tool's arguments rather than through its name. It also cannot detect a built-in the manifest itself omits: it proves the accounting closes over what we listed, not over what exists.

**Honest limit on this instrument as written.** `test/release/surface-enumeration.test.ts` does not exist yet, so today's failure is a missing file rather than a failing assertion — the weak form of red, filed as `no-spec`, minting no build permit. The unattended surface that wrote this cannot create the file: `Write` is denied to it, deliberately. The assertion is specified above in enough detail to be written without re-deriving it, and the test is not finished until that spec exists and its accounting assertion is what fails.

## Instrument Log
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/release/surface-enumeration.test.ts` — test/release/surface-enumeration.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/release/surface-enumeration.test.ts` — test/release/surface-enumeration.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/release/surface-enumeration.test.ts` — test/release/surface-enumeration.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/release/surface-enumeration.test.ts` — test/release/surface-enumeration.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/release/surface-enumeration.test.ts` — test/release/surface-enumeration.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/release/surface-enumeration.test.ts` — test/release/surface-enumeration.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/release/surface-enumeration.test.ts` — test/release/surface-enumeration.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/release/surface-enumeration.test.ts` — test/release/surface-enumeration.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/release/surface-enumeration.test.ts` — test/release/surface-enumeration.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/release/surface-enumeration.test.ts` — test/release/surface-enumeration.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/release/surface-enumeration.test.ts` — test/release/surface-enumeration.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/release/surface-enumeration.test.ts` — test/release/surface-enumeration.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/release/surface-enumeration.test.ts` — test/release/surface-enumeration.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/release/surface-enumeration.test.ts` — test/release/surface-enumeration.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/release/surface-enumeration.test.ts` — test/release/surface-enumeration.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/release/surface-enumeration.test.ts` — test/release/surface-enumeration.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/release/surface-enumeration.test.ts` — test/release/surface-enumeration.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/release/surface-enumeration.test.ts` — test/release/surface-enumeration.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/release/surface-enumeration.test.ts` — test/release/surface-enumeration.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/release/surface-enumeration.test.ts` — test/release/surface-enumeration.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/release/surface-enumeration.test.ts` — test/release/surface-enumeration.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/release/surface-enumeration.test.ts` — test/release/surface-enumeration.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/release/surface-enumeration.test.ts` — test/release/surface-enumeration.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/release/surface-enumeration.test.ts` — test/release/surface-enumeration.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/release/surface-enumeration.test.ts` — test/release/surface-enumeration.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/release/surface-enumeration.test.ts` — test/release/surface-enumeration.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/release/surface-enumeration.test.ts` — test/release/surface-enumeration.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/release/surface-enumeration.test.ts` — test/release/surface-enumeration.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/release/surface-enumeration.test.ts` — test/release/surface-enumeration.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/release/surface-enumeration.test.ts` — test/release/surface-enumeration.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/release/surface-enumeration.test.ts` — test/release/surface-enumeration.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/release/surface-enumeration.test.ts` — test/release/surface-enumeration.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/release/surface-enumeration.test.ts` — test/release/surface-enumeration.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/release/surface-enumeration.test.ts` — test/release/surface-enumeration.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/release/surface-enumeration.test.ts` — test/release/surface-enumeration.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/release/surface-enumeration.test.ts` — test/release/surface-enumeration.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/release/surface-enumeration.test.ts` — test/release/surface-enumeration.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/release/surface-enumeration.test.ts` — test/release/surface-enumeration.test.ts does not exist — no spec was collected, so nothing was measured
