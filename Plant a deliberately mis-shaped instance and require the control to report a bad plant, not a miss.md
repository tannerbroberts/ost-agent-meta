---
type: AssumptionTest
source: 'agent-ideation:2026-08-09-unattended-sweep'
created: '2026-08-10'
evidence: assertion
threshold: >-
  A mis-shaped plant produces a distinct bad-plant verdict, never a sweep-miss
  verdict, on every seeded sweep. One mis-shaped plant reported as a sweep miss
  fails the test, because that is the false alarm the 2026-07-27 run produced
  three of.
instrument: npx vitest run test/ost/positive-control-plant-shape.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: feasibility.**

**What this measures.** Whether a positive control has two distinguishable failure outputs or one. Not whether the sweeps work — that was answered on 2026-07-27, 12 plants and 12 found — but whether the control can be trusted when it says something is wrong.

**The assertion the spec makes,** written out so this is a designed test rather than a reserved path. Using `test/ost/fixture-vault.ts`, for a seeded sweep:

1. **Clean baseline.** Run the sweep on a vault with no plant and assert it reports zero findings. This is the half the solution body asks for first, and it is what stops a control from passing because the vault was already dirty in the shape being planted.
2. **Good plant found.** Seed an instance the rule provably matches and assert the sweep finds it. This is the 2026-07-27 assertion, kept so the new behaviour cannot be bought by breaking the old one.
3. **Mis-shaped plant is named as such.** Seed an instance the rule does **not** match — the exact defect that produced all three apparent misses in that run — and assert the harness returns a verdict distinguishable from a sweep miss. Not a different message: a different outcome value, so a caller can branch on it rather than parse prose.
4. **The two are never conflated.** Assert a sweep-miss verdict is only ever produced when the plant validated as well-shaped, so the bad-plant case cannot silently fall through into it.

Assertion 3 is the load-bearing one. Assertion 1 and 2 exist so it cannot be satisfied by a harness that calls everything a bad plant.

**Why it is red today, and which kind of red.** A `no-spec` red, stated plainly rather than left to be found. `test/ost/positive-control-plant-shape.test.ts` does not exist, and no plant or seeding mechanism exists in `src/ost/census.ts` or `src/ost/stranded.ts` — verified by reading `census.ts` in full this pass. So the command fails first on the missing file, which the ruleset files as granting no build permit on its own. An unattended pass has read-only repo sight: it can name the module and write the assertion, and it cannot leave the spec file behind. The remaining step is a builder's, and it is small because the assertions are specified above.

**Why it is small.** One fixture vault, one sweep, three seedings. The fixture helper already exists.

**What this does NOT settle, so a green is not over-read.** Passing proves the control distinguishes a bad plant from a blind check. It does not prove the sweeps are correct — that is the sibling belief, and it already has a recorded run. It does not address the solution's own stated weakness, that "a control chosen from the same source the sweep reads can be blind in the same way", which is the false-negative direction and needs an independently established fixture rather than a shape assertion. And it says nothing about the maintenance cost the solution names — "keeping such fixtures current is real maintenance nobody has budgeted" — which is a question about people's time, not about code.

**Standing do-not-build is untouched.** The 2026-07-27 result put this solution behind the existing verify-failing-first discipline by its own pre-commitment, and nothing here promotes it. This gives the narrower version a runnable form for whenever it is picked up.

⚠️ Unvalidated. Agent-ideated; no test was run and no result is recorded.

## Instrument Log
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/ost/positive-control-plant-shape.test.ts` — test/ost/positive-control-plant-shape.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/ost/positive-control-plant-shape.test.ts` — test/ost/positive-control-plant-shape.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/ost/positive-control-plant-shape.test.ts` — test/ost/positive-control-plant-shape.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/ost/positive-control-plant-shape.test.ts` — test/ost/positive-control-plant-shape.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/ost/positive-control-plant-shape.test.ts` — test/ost/positive-control-plant-shape.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/ost/positive-control-plant-shape.test.ts` — test/ost/positive-control-plant-shape.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/ost/positive-control-plant-shape.test.ts` — test/ost/positive-control-plant-shape.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/ost/positive-control-plant-shape.test.ts` — test/ost/positive-control-plant-shape.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/ost/positive-control-plant-shape.test.ts` — test/ost/positive-control-plant-shape.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/ost/positive-control-plant-shape.test.ts` — test/ost/positive-control-plant-shape.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/ost/positive-control-plant-shape.test.ts` — test/ost/positive-control-plant-shape.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/ost/positive-control-plant-shape.test.ts` — test/ost/positive-control-plant-shape.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/ost/positive-control-plant-shape.test.ts` — test/ost/positive-control-plant-shape.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/ost/positive-control-plant-shape.test.ts` — test/ost/positive-control-plant-shape.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/ost/positive-control-plant-shape.test.ts` — test/ost/positive-control-plant-shape.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/ost/positive-control-plant-shape.test.ts` — test/ost/positive-control-plant-shape.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/ost/positive-control-plant-shape.test.ts` — test/ost/positive-control-plant-shape.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/ost/positive-control-plant-shape.test.ts` — test/ost/positive-control-plant-shape.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/ost/positive-control-plant-shape.test.ts` — test/ost/positive-control-plant-shape.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/ost/positive-control-plant-shape.test.ts` — test/ost/positive-control-plant-shape.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/ost/positive-control-plant-shape.test.ts` — test/ost/positive-control-plant-shape.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/ost/positive-control-plant-shape.test.ts` — test/ost/positive-control-plant-shape.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/ost/positive-control-plant-shape.test.ts` — test/ost/positive-control-plant-shape.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/ost/positive-control-plant-shape.test.ts` — test/ost/positive-control-plant-shape.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/ost/positive-control-plant-shape.test.ts` — test/ost/positive-control-plant-shape.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/ost/positive-control-plant-shape.test.ts` — test/ost/positive-control-plant-shape.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/ost/positive-control-plant-shape.test.ts` — test/ost/positive-control-plant-shape.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/ost/positive-control-plant-shape.test.ts` — test/ost/positive-control-plant-shape.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/ost/positive-control-plant-shape.test.ts` — test/ost/positive-control-plant-shape.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/ost/positive-control-plant-shape.test.ts` — test/ost/positive-control-plant-shape.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/ost/positive-control-plant-shape.test.ts` — test/ost/positive-control-plant-shape.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/ost/positive-control-plant-shape.test.ts` — test/ost/positive-control-plant-shape.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/ost/positive-control-plant-shape.test.ts` — test/ost/positive-control-plant-shape.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/ost/positive-control-plant-shape.test.ts` — test/ost/positive-control-plant-shape.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/ost/positive-control-plant-shape.test.ts` — test/ost/positive-control-plant-shape.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/ost/positive-control-plant-shape.test.ts` — test/ost/positive-control-plant-shape.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/ost/positive-control-plant-shape.test.ts` — test/ost/positive-control-plant-shape.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/ost/positive-control-plant-shape.test.ts` — test/ost/positive-control-plant-shape.test.ts does not exist — no spec was collected, so nothing was measured
