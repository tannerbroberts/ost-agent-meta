---
type: AssumptionTest
created: '2026-08-06'
evidence: assertion
threshold: >-
  All three profiles resolve to their real grants, and an argument-level
  restriction is either expressible or raises an explicit unsupported error.
instrument: npx vitest run test/config/surface-profile.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Assumption under test (feasibility).** That the difference between surfaces is a tool list, and not something finer that a list cannot hold.

**The test.** Declare `unattended`, `attended` and `ci` profiles in config, load each, and assert the resolved tool set matches the surface's real grants. Then assert the profile can express one argument-level restriction — a tool present but refusing a reserved heading — and fails loudly rather than silently claiming full access when it cannot.

**Pre-commit before running:** all three profiles must resolve to their real grants, and the argument-level case must either be expressible or produce an explicit unsupported error. A profile that resolves cleanly while quietly dropping the restriction refutes this, because that is the false-assurance failure the assumption names.

**What this does NOT settle.** Whether an operator will keep three profiles current as grants change. A stale profile is confidently wrong, which the solution node names as its own worst outcome, and only usage over time reports on it.

**Lane: compute-only.**

⚠️ Proposed only — the agent does not run tests or record results.

## Instrument Log
- 2026-08-06 **red** (exit 1) `npx vitest run test/config/surface-profile.test.ts` — No test files found, exiting with code 1
