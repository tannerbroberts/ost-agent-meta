---
type: AssumptionTest
created: '2026-08-06'
evidence: assertion
threshold: >-
  All four real declines express as conditions that evaluate to a boolean
  against the tree alone, and all four revive when flipped; one prose-only
  condition refutes.
instrument: npx vitest run test/ost/suppression-condition.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Assumption under test (feasibility).** That the conditions worth suppressing on are machine-checkable, so a suppression revives on a fact rather than on nobody noticing.

**The test.** Take four declines this vault has actually produced — a solution declined because it is shipped, a test declined because it needs people outside the building, an item declined because the surface lacked the tool, an unknown declined for want of a Format — and express each as a condition. Assert every one evaluates to a boolean against the tree alone, and assert an item whose condition has flipped is offered again on the next call.

**Pre-commit before running:** all four must evaluate mechanically and all four must revive when flipped. If any of the four can only be stated in prose, this is refuted and the suppression must be refused rather than shipped with an unevaluable escape hatch — that case is the delete the surface withholds, wearing a different name.

**What this does NOT settle.** Whether agents choose honest conditions when unobserved. A spec proves an evaluable condition revives; it says nothing about an agent picking a condition that will never flip, which is the actual abuse and needs a human reading suppressions over time.

**Lane: compute-only.**

⚠️ Proposed only — the agent does not run tests or record results.

## Instrument Log
- 2026-08-07 **red** (exit 1) `npx vitest run test/ost/suppression-condition.test.ts` — No test files found, exiting with code 1
- 2026-08-12 **green** (exit 0) `npx vitest run test/ost/suppression-condition.test.ts` — ✓ fail-open, both directions: a hand-damaged ledger line suppresses nothing, and a condition whose node left the tree stops holding 335ms
