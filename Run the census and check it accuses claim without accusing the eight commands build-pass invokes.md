---
type: AssumptionTest
source: >-
  INBOX:friction/2026-08-10-friction-pr-80-shipped-a-pass-claims-the-work-item-before.md
created: '2026-08-10'
evidence: assertion
threshold: >-
  The census output contains `claim` and contains none of `gate`, `buildable`,
  `verify`, `check`, `debt`, `loop health`. One false accusation among those six
  fails the test.
instrument: npx vitest run test/product/caller-census.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.** The subject is this repository and the measurement is an exit code; no person is the instrument.

**What the spec asserts.** Point the census at this repository's own `src/` and `examples/`. Assert two things, and the second is the one that can fail:
1. `claim` appears in the unreached list. This is the easy half — it is unreached, and any implementation finds it.
2. None of `gate`, `buildable`, `verify`, `check`, `debt` or `loop health` appears. These six are reached only through `node "$CLI" <subcommand>` string interpolation inside `examples/automation/build-pass.sh`, verified by reading that script this pass. A census that reads TypeScript imports and nothing else reports all six as unreached and fails here.

That second assertion is the whole test. It is chosen because it is the cheapest available instance of the failure mode the assumption names — a walk that cannot see shell callers — and because the six names are a fixed, already-verified fact rather than a fixture the spec author gets to choose.

**Why it is red today, stated precisely.** `test/product/caller-census.test.ts` does not exist and no census module exists for it to import, so today's run is filed as **`no-spec`** and mints no build permit. That is the weakest kind of red and this node says so rather than letting a reader mistake it for a measurement: it fails identically for every question anyone could write on that path. It becomes a real red the moment the spec is written against a census that only reads imports, and green when the walk also reads the shell scripts.

**What a green here does not settle.** Nothing about whether unreached code is common — that is the number the census exists to produce and this only checks the instrument can produce it. Nothing about the deeper false-negative direction either: code called only from other dead code counts as reached under any caller-counting scheme, and this test does not probe that at all. And nothing about whether an operator reads the report.

⚠️ Unvalidated. Agent-proposed; not run.

## Instrument Log
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/product/caller-census.test.ts` — test/product/caller-census.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/product/caller-census.test.ts` — test/product/caller-census.test.ts does not exist — no spec was collected, so nothing was measured
