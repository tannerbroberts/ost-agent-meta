---
type: AssumptionTest
source: 'agent-ideation:2026-08-22-unattended-sweep'
created: '2026-08-22'
evidence: assertion
threshold: >-
  0 of 3 set-instrument calls made with no configured product repo are accepted,
  and 3 of 3 calls naming a resolvable spec on the same vault still write — both
  halves in one run.
instrument: npx vitest run test/instruments/blind-instrument-refusal.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**What this measures.** Whether the write boundary can refuse the blind case *narrowly* — refusing an instrument written with no repo to resolve against, while still writing one whose spec resolves. Both halves must hold in a single run; a spec that only proves the refusal would be satisfied by a boundary that refuses everything, which is the failure mode the current code was written to avoid.

**Why it is red today, and red for a reason specific to this test.** The behaviour does not merely not exist — the repository asserts its opposite. `test/instruments/spec-path-resolution.test.ts` contains the describe block "with no product repo configured, the guard stands down", whose single case expects an unresolvable path to be **accepted** when `productRepos` is `[]`. So the first half of this threshold is contradicted by a committed, passing spec. Change this test's question and the red goes away; that is what makes it a measurement rather than a filename.

**What the spec has to do, so the builder is not handed a blank file.** Build the vault fixture the existing spec already builds (`initVault`, then `buildOstTools({...ctx, productRepos}, MCP_TOOL_NAMES)`), and assert both directions against it:

- with `productRepos: []`, three `ost_set_instrument` calls — an unresolvable path, a resolvable-looking path, and one carrying a bound threshold — all reject, and each message names the missing repo configuration rather than the missing file;
- with `productRepos: [repo]`, a call naming `test/exists.test.ts` still writes, and `vault.read(LEGACY).instrument` holds it.

The builder's first real decision is what happens to the existing stand-down case, and it is a decision rather than a detail: it is currently correct and reasoned, so either it is deleted with its rationale answered, or this solution is wrong. Either outcome is worth more than the queue entry was.

**Lane: compute-only.** The whole question is what a write boundary does with a config value, and no part of it involves a person.

**What a green here does NOT settle.** Only feasibility. It says nothing about whether operators would rather have an honest gap than a guessed command — that is the sibling assumption, it needs people, and a passing spec here must not be read as evidence for it. It also says nothing about the throughput cost the solution's own body flags as an unknown exchange rate: a boundary that refuses correctly can still refuse so often that the queue never moves, and this spec cannot see that.

**Provenance note.** Written by an unattended pass that held repo sight; every claim above about current behaviour was read from `src/ost/instrument.ts`, `src/knowledge/instruments.ts` and `test/instruments/spec-path-resolution.test.ts` this pass, not remembered.

## Instrument Log
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-24 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-24 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-25 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-26 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-26 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-26 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-27 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-27 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-27 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-27 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-27 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-27 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-28 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-28 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-28 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-28 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-28 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-28 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-28 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-28 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-29 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-29 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-29 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-29 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-29 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-29 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-29 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-29 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-30 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-30 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-30 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-30 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-30 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-30 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/instruments/blind-instrument-refusal.test.ts` — test/instruments/blind-instrument-refusal.test.ts does not exist — no spec was collected, so nothing was measured
