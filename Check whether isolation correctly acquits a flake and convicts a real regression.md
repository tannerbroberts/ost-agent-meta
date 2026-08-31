---
type: AssumptionTest
source: 'agent-ideated:2026-08-02-maintenance-pass'
created: '2026-08-02'
evidence: assertion
instrument: npx vitest run test/runner/flake-attribution.test.ts
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: feasibility.** Whether the re-run is a fair judge.

**The assumption under test.** That "passes in isolation" reliably means "was a flake." The candidate's own objection is the dangerous case: an operation slow *because* of a genuine regression under concurrency would pass in isolation and be labelled a flake, silently. That is a false acquittal, and it is worse than the problem being solved — the current state at least shows a red that a human investigates.

**The test (three scenarios, known answers).** For each, run the suite, let the timing assertion fail or pass, then apply re-run-and-attribute and check the label:

1. **Known flake** — reproduce the 2026-08-01 conditions (full 141-file suite under load). Correct label: *contention*.
2. **Known regression, load-independent** — plant a fixed slowdown. Correct label: *regression*, and it must survive the isolated re-run.
3. **Known regression, concurrency-only** — plant a slowdown that manifests only under parallel execution (lock contention or a shared resource is the realistic shape). Correct label: *regression*. **This is the scenario that decides the candidate.**

**Pre-committed threshold.** All three labelled correctly, **3 of 3 repetitions each**. Scenario 3 is not negotiable: if the mechanism cannot convict a concurrency-only regression, it must not be built in this form, because the failure it introduces is silent and the failure it removes is loud.

**A cheaper partial answer if scenario 3 fails.** Report the disagreement without resolving it — *"failed in suite, passed in isolation; cause not determined"* — rather than asserting *contention*. That keeps the attribution information and drops the unearned verdict, and it is what the candidate should be rewritten to if this test comes out mixed. Recorded here so a failed test still leaves something buildable rather than only a closed branch.

**Who runs it.** A human, or an attended session with a build environment.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/runner/flake-attribution.test.ts — Plants the node's three scenarios with known answers — a load-induced flake, a load-independent regression, and the deciding case of a concurrency-only regression — and asserts re-run-and-attribute labels all three correctly on 3 of 3 repetitions each. It fails today because no re-run-and-attribute mechanism exists, so nothing can return a label to check.

## Instrument Log
- 2026-08-04 **red** (exit 1) `npx vitest run test/runner/flake-attribution.test.ts` — No test files found, exiting with code 1
- 2026-08-31 **green** (exit 0) `npx vitest run test/runner/flake-attribution.test.ts` — Duration  7.24s (transform 96ms, setup 0ms, collect 144ms, tests 6.86s, environment 0ms, prepare 28ms)
