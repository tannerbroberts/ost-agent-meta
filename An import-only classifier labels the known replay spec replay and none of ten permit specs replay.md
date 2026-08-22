---
type: AssumptionTest
source: 'agent-ideation:2026-08-20-unattended-sweep'
created: '2026-08-20'
evidence: assertion
threshold: >-
  1 of 1 known replay spec (test/loop/question-stop-independence-replay.test.ts)
  classifies as replay, and 0 of 10 sampled specs from test/ost classify as
  replay
instrument: npx vitest run test/instruments/replay-kind-classification.test.ts
sight: grounded
---
#AssumptionTest #unvalidated #evidence/assertion

**What the spec asserts.** A function beside `parseInstrument` in `src/knowledge/instruments.ts` (or beside `runInstrument` in `src/ost/instrument.ts`) reads a spec file's import statements only and returns `replay` or `permit`. Assert it returns `replay` for `test/loop/question-stop-independence-replay.test.ts` — the one spec in the suite this pass could identify as replaying recorded sessions against a bar — and `permit` for each of ten specs sampled from `test/ost/` (e.g. `instrument.test.ts`, `results.test.ts`, `lanes.test.ts`, `mutate.test.ts`, `extent.test.ts`, `dedupe.test.ts`, `census.test.ts`, `vault.test.ts`, `node.test.ts`, `sanitize.test.ts`). If the named replay spec turns out not to be the stop-count replay the PR #130 builder wrote, substitute that spec; the claim is about the kind, not the filename.

**Lane: compute-only.**

**Why it is red today, and what kind of red.** `test/instruments/replay-kind-classification.test.ts` does not exist — a **no-spec red**, declared as such; it mints no permit until the spec exists and fails on an assertion. Once written it fails on the import: no classifier exists, and `Observation` in `src/ost/instrument.ts` has three members, none of them a finding.

**What a green does NOT settle.** That imports separate the two kinds on eleven files says nothing about a spec that is both (fixture plus new code path), nothing about the harness-unbuilt phase where a replay spec is legitimately a permit red, and nothing about whether `buildable` should read `refuted` as not-a-permit — that is the solution's second half and needs its own assertion. Feasibility of the heuristic only.

## Instrument Log
- 2026-08-20 **no-spec** (exit none) `npx vitest run test/instruments/replay-kind-classification.test.ts` — test/instruments/replay-kind-classification.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-21 **no-spec** (exit none) `npx vitest run test/instruments/replay-kind-classification.test.ts` — test/instruments/replay-kind-classification.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-21 **no-spec** (exit none) `npx vitest run test/instruments/replay-kind-classification.test.ts` — test/instruments/replay-kind-classification.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-21 **no-spec** (exit none) `npx vitest run test/instruments/replay-kind-classification.test.ts` — test/instruments/replay-kind-classification.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-21 **no-spec** (exit none) `npx vitest run test/instruments/replay-kind-classification.test.ts` — test/instruments/replay-kind-classification.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-21 **no-spec** (exit none) `npx vitest run test/instruments/replay-kind-classification.test.ts` — test/instruments/replay-kind-classification.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-21 **no-spec** (exit none) `npx vitest run test/instruments/replay-kind-classification.test.ts` — test/instruments/replay-kind-classification.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-21 **no-spec** (exit none) `npx vitest run test/instruments/replay-kind-classification.test.ts` — test/instruments/replay-kind-classification.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-21 **no-spec** (exit none) `npx vitest run test/instruments/replay-kind-classification.test.ts` — test/instruments/replay-kind-classification.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-21 **no-spec** (exit none) `npx vitest run test/instruments/replay-kind-classification.test.ts` — test/instruments/replay-kind-classification.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/instruments/replay-kind-classification.test.ts` — test/instruments/replay-kind-classification.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/instruments/replay-kind-classification.test.ts` — test/instruments/replay-kind-classification.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/instruments/replay-kind-classification.test.ts` — test/instruments/replay-kind-classification.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/instruments/replay-kind-classification.test.ts` — test/instruments/replay-kind-classification.test.ts does not exist — no spec was collected, so nothing was measured
