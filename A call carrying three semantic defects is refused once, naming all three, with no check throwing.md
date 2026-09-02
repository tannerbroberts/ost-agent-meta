---
type: AssumptionTest
source: 'agent-ideation:2026-08-30-unattended-sweep'
created: '2026-08-30'
evidence: assertion
threshold: >-
  at least 3 of 3 defects named in a single refusal, and exactly 0 checks
  throwing on already-rejected input
instrument: npx vitest run test/mcp/semantic-problems-accumulate.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.** A temp vault and assertions about one response; nothing outside the process is involved.

**What the spec must assert.** Build the scaffold from `test/mcp/tool-input-validation.test.ts` — `initVault`, `createLazyOstMcpServer`, `InMemoryTransport.createLinkedPair()` — then:

1. One `ost_create_node` call for an AssumptionTest violating three semantic rules at once (threshold with no comparator, instrument carrying shell punctuation, parent of the wrong layer) is refused **once**, and the refusal text names all three.
2. The refusal is rendered in the same shape the schema layer already uses — one bullet per problem — so a caller does not have to parse two different refusal formats depending on which layer objected.
3. **The order is the ranked order, not arbitrary.** Seed a call that is both disqualified (a lane that forbids the write outright) and malformed, and assert the disqualifying objection is printed first. This is what stops a caller fixing the cheap defect and re-issuing a call that was doomed either way.
4. **No check throws on input an earlier check rejected.** Drive each semantic check with a deliberately malformed argument that an earlier check would previously have short-circuited on, and assert a refusal rather than an unhandled error.

**Assertion 4 is the one this test exists for.** Assertions 1–3 describe the feature; 4 is the assumption. Short-circuiting on the first `throw` currently doubles as a guard, and a builder converting the layer to an accumulator gets 1–3 working long before discovering which checks quietly relied on never seeing garbage. A crash on a malformed call is strictly worse than today's serialised refusal, because the caller learns nothing at all.

**Why it fails today, stated honestly.** `test/mcp/semantic-problems-accumulate.test.ts` does not exist, so this run files as `no-spec` and mints no permit — the weak red form, forced by the behaviour being unbuilt rather than chosen. The four assertions and the named template are what the instrument contributes beyond a filename.

**What a green would NOT settle.** Whether multi-defect calls are common enough to be worth the per-check rework. Two sessions are on record — `fe8409a0` and `14f184b4` — and no census has been run, so this could be a refactor across every check for a case that rarely fires. It also says nothing about whether the hand-kept severity ranking gets maintained, which is the candidate's other admitted cost and is a question about a person, not an exit code.

## Instrument Log
- 2026-08-30 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-30 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-30 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-30 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-02 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-02 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-02 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-02 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-02 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-02 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-02 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-02 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-02 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-02 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-02 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-02 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-02 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-02 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-02 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-02 **no-spec** (exit none) `npx vitest run test/mcp/semantic-problems-accumulate.test.ts` — test/mcp/semantic-problems-accumulate.test.ts does not exist — no spec was collected, so nothing was measured
