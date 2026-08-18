---
type: AssumptionTest
status: unvalidated
created: '2026-08-02'
evidence: assertion
threshold: >-
  All five files keep every setting they started with, and at least four of the
  five remain valid without hand-fixing.
instrument: npx vitest run test/config/settings-merge-safety.test.ts
---
#AssumptionTest #feasibility #unvalidated #evidence/assertion

**The assumption under test (feasibility):** that setup can write its enabling configuration into a project the operator already owns without damaging what is there. If merging is unsafe, this candidate is not a setup-time fix at all — it is a way to break people's existing configuration at the exact moment they are trying the product for the first time.

**How it would run:** take five real settings files from projects that already have one, including at least one that already enables other plugins and one with comments or unusual formatting. Apply the merge to a copy of each. Compare before and after.

**Why it is the riskiest thing here:** the candidate's value is that it removes the failure rather than detecting it, and that value survives only if the write is safe. Everything else about this solution is straightforward.

Half a day, retrospective, no build beyond the merge itself. Proposed by the agent; a human runs it and records the outcome.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/config/settings-merge-safety.test.ts — The threshold — all five files keep every setting they started with, and at least four remain valid without hand-fixing — is a property of committed code: the spec carries five settings fixtures (one already enabling other plugins, one with comments and unusual formatting), applies the merge to each, and asserts every original key survives with its value and that at least four still parse. It fails today because no merge routine exists.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/config/settings-merge-safety.test.ts` — No test files found, exiting with code 1
- 2026-08-18 **green** (exit 0) `npx vitest run test/config/settings-merge-safety.test.ts` — Duration  214ms (transform 21ms, setup 0ms, collect 22ms, tests 7ms, environment 0ms, prepare 28ms)
