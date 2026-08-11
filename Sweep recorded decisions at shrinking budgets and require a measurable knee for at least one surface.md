---
type: AssumptionTest
created: '2026-08-11'
evidence: assertion
threshold: >-
  For at least one real surface, the sweep over recorded decisions reports a
  knee: a budget below which the verdict-flip rate crosses 5% while remaining
  under 1% at the full budget.
instrument: npx vitest run test/compression/budget-knee.test.ts
---
#AssumptionTest #compression #unvalidated #evidence/assertion

Replay the vault's recorded decision pairs (evidence record → mapping outcome; tree state → rollup verdict) at a descending ladder of byte budgets and compute the verdict-flip rate per budget. The spec passes when the sweep produces a monotone-enough fidelity curve with an identifiable knee for at least one real surface; it fails (and the assumption with it) if the curve is flat across the whole measured range or too noisy to place a knee.
