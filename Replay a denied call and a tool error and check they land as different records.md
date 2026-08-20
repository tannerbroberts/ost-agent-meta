---
type: AssumptionTest
created: '2026-08-06'
evidence: assertion
threshold: >-
  Both kinds classify correctly, and both still classify correctly after their
  message strings are rewritten.
instrument: npx vitest run test/adapters/usage-denial-classification.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Assumption under test (feasibility).** That a permission denial and a tool's own error are separable at capture, without pattern-matching on host wording.

**The test.** Feed the usage adapter two recorded invocations: one denied for lack of a grant, one failing on its own terms (the 2026-08-05 `ost_read_repo` "no product repos configured" error is a real specimen of the second). Assert they are classified into different kinds, and assert the classification does not depend on the prose of the message — change the wording of both and the verdict must not move.

**Pre-commit before running:** both must classify correctly, and both must still classify correctly after their message strings are rewritten. If the wording-independence half fails, this is a string matcher wearing a classifier's name and should be refuted.

**What this does NOT settle.** Whether recorded refusals ever change what a later pass does. That is the whole value of the solution and it needs passes over time, not a spec. Feasibility answered here leaves desirability exactly where it was.

**Lane: compute-only.**

⚠️ Proposed only — the agent does not run tests or record results.

## Instrument Log
- 2026-08-06 **red** (exit 1) `npx vitest run test/adapters/usage-denial-classification.test.ts` — No test files found, exiting with code 1
- 2026-08-20 **green** (exit 0) `npx vitest run test/adapters/usage-denial-classification.test.ts` — Duration  295ms (transform 41ms, setup 0ms, collect 45ms, tests 7ms, environment 0ms, prepare 32ms)
