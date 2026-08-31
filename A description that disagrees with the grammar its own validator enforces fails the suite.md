---
type: AssumptionTest
source: 'agent-run:unattended-sweep-2026-08-27'
created: '2026-08-27'
evidence: assertion
threshold: >-
  every example command quoted in a tool description parses, and at least 1
  seeded mismatch fails the suite
instrument: npx vitest run test/mcp/description-grammar-parity.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: feasibility. Small and fast: it reads two artefacts already in the repository and compares them.**

Take every command-shaped example quoted in an `ost_*` tool description and run it through `parseInstrument` from `src/knowledge/instruments.ts`. Each must come back as an instrument rather than a rejection. Then seed the mismatch deliberately — a description quoting a form the validator does not accept, such as one carrying a `-t` filter — and assert the check fails on it, so the parity test cannot pass vacuously.

The positive control is the part worth insisting on. A parity check that finds nothing looks identical to one with nothing to find, and this vault has already been bitten by that shape: `test/ost/vault-write-guard.test.ts` carries an explicit "the guard cannot pass vacuously" block for the same reason, and the `no-spec` classification exists because a red that every question would produce distinguishes none of them.

**Why it is red today.** No such check exists — nothing in the suite reads a tool description at all, so no artefact today asserts the two agree. It goes green when the parity check is written and the descriptions are made to satisfy it.

**Honest labelling of how red it is.** `test/mcp/description-grammar-parity.test.ts` does not exist, so the first run is filed `no-spec` rather than a true red, and would fail identically for any question written on that path. `test/mcp/` is a real, populated directory, and the threshold above is a bound bar with a positive control in it — the two properties this vault's own 2026-08-09 and 2026-08-21 findings identify as what separates a weak red a builder can act on from one they cannot. The stronger form, naming an assertion inside an existing spec, is not expressible: the instrument grammar accepts a bare `npx vitest run <path>.test.ts` and rejects a `-t` filter as shell punctuation.

**A note on what this test is an instance of.** The candidate it serves proposes publishing a grammar; this test's own instrument was constrained by that same grammar being unpublished and discovered by refusal. That is not irony worth much, but it is one more first-party sighting of the refusal class the parent opportunity is about, and it happened during the pass that wrote this node.

**What a green does not settle.** Whether publishing the grammar stops the refusal — that depends on a session reading the description before composing, which is a usability question about the reader and needs a separate test. It also covers only grammars statable in advance, so it says nothing about the state-dependent refusals (the humans-required lane) that this candidate admits it cannot reach.

## Instrument Log
- 2026-08-27 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-28 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-28 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-28 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-28 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-28 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-28 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-28 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-28 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-29 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-29 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-29 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-29 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-29 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-29 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-29 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-29 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-30 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-30 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-30 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-30 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-30 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-30 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
