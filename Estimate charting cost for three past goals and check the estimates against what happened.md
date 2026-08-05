---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  Both estimators land within a factor of 2 of the actual on at least 2 of 3
  goals.
instrument: npx vitest run test/cli/chart-cost-estimate.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that charting cost can be estimated well enough to inform a choice. A bad estimate is worse than none, because it will be wrong in the direction that justifies whatever was already wanted, and there is no obvious way to calibrate it in advance.

**Risk category: feasibility.**

**Design.** Take three goals this project has already charted, and have someone estimate — from the goal statement alone, without looking at what happened — how much evidence, how many conversations, and how long before the first branch was actionable. Then compare against the record. Repeat with a second estimator to see whether the errors are shared or personal.

**Why it is small.** The outcomes are already in the vault; only the estimates are new, and each is a few minutes.

**What it will not cover.** Three goals is a very small sample, and an estimator who has worked on this project cannot fully unsee what happened. The second estimator is what makes it worth running at all.

A human runs this and records the result.

## History
- 2026-08-05 instrument: (none) → npx vitest run test/cli/chart-cost-estimate.test.ts — Checking an estimate against what happened requires the estimate to have been recorded before the goal was chosen, and nothing today captures one — so every such comparison is reconstructed after the fact, which is the drift this solution exists to prevent. This asserts the capture: setting an outcome records a dated charting-cost estimate alongside it, the estimate is written before the outcome is committed rather than appended afterwards, and the rollup reports estimate against actual spend for each goal so the comparison is computed rather than remembered. Missing-spec red, not assertion red — no cost estimate is captured anywhere, so the command fails on a missing file; a builder should write it against the real set-outcome path so it goes red on an outcome accepted with no estimate. It does not settle whether the estimates were any GOOD for the three past goals, which is a person's retrospective judgement and stays with a human.
