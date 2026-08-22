---
type: AssumptionTest
source: 'agent-ideation:2026-08-21-unattended-sweep'
created: '2026-08-21'
evidence: assertion
threshold: >-
  All 3 assertions in test/config/probe-spec-by-name-only.test.ts pass: (1)
  vitest.config.ts's `exclude` covers `**/*.probe.test.ts` unless a
  `.probe.test.ts` file is named on the command line; (2) with a fixture
  `test/config/__fixture.probe.test.ts` present, `npx vitest run
  --reporter=json` lists 0 files matching `.probe.test.ts`, and `npx vitest run
  test/config/__fixture.probe.test.ts --reporter=json` lists exactly 1; (3)
  .gitignore contains a `*.probe.test.ts` line.
instrument: npx vitest run test/config/probe-spec-by-name-only.test.ts
sight: grounded
---
#AssumptionTest #feasibility #build-loop #unvalidated #evidence/assertion

**Lane: compute-only.** A spec that spawns the repo's own test runner twice and compares the file lists settles it; nobody outside the building is the measurement.

**What the spec must assert, stated so the next reader does not inherit a blank file.**

1. Read `vitest.config.ts`; expect the source to reference `probe.test.ts` inside the `exclude` construction and to route it through the existing `namedOnCommandLine` check (a regex over the config text, in the style `test/automation/build-pass-reports.test.ts` uses on shell source). Today the config excludes `configDefaults.exclude` plus one `CONTENDED` file and mentions no probe glob — read this pass via `ost_read_repo`.
2. Write `test/config/__fixture.probe.test.ts` containing one passing `test()`, then `execFileSync("npx", ["vitest", "run", "--reporter=json"], { cwd: root })` and parse `testResults[].name`: expect no entry ending in `.probe.test.ts`. Then run again with the fixture path as an extra argument and expect exactly 1 such entry, passing. Remove the fixture in `finally`. This is the assertion that carries the belief, and the one the config's own comment predicts is non-trivial: "vitest applies `exclude` before CLI filters, so an excluded file cannot be reached by naming it" — if the argv gate does not generalise from a literal filename to a glob, the second run lists 0 and the assumption is refuted.
3. `.gitignore` contains a line `*.probe.test.ts`. Today it does not.

**Why it is red today, honestly classified.** The spec file does not exist, so today's red is `no-spec` — it would fail identically for any question written on this path and grants no build permit. It becomes a real red the moment the spec above is written: assertion (1) fails against the current config and (3) against the current `.gitignore`. A pass on this surface can name the mechanism but cannot leave the spec behind; the deliverable is the failing spec, not this filename.

**What a green does NOT settle.** Whether a probe dressed as a spec gets committed as one by a session that forgot it was throwaway (habit, observed over firings); whether the argv gate survives the next vitest major (a future red, not today's); and whether anyone wanted the lost turn back (desirability).

## Instrument Log
- 2026-08-21 **no-spec** (exit none) `npx vitest run test/config/probe-spec-by-name-only.test.ts` — test/config/probe-spec-by-name-only.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-21 **no-spec** (exit none) `npx vitest run test/config/probe-spec-by-name-only.test.ts` — test/config/probe-spec-by-name-only.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-21 **no-spec** (exit none) `npx vitest run test/config/probe-spec-by-name-only.test.ts` — test/config/probe-spec-by-name-only.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-21 **no-spec** (exit none) `npx vitest run test/config/probe-spec-by-name-only.test.ts` — test/config/probe-spec-by-name-only.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-21 **no-spec** (exit none) `npx vitest run test/config/probe-spec-by-name-only.test.ts` — test/config/probe-spec-by-name-only.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-21 **no-spec** (exit none) `npx vitest run test/config/probe-spec-by-name-only.test.ts` — test/config/probe-spec-by-name-only.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/config/probe-spec-by-name-only.test.ts` — test/config/probe-spec-by-name-only.test.ts does not exist — no spec was collected, so nothing was measured
