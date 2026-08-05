---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Estimate charting cost for three past goals and check the estimates against what happened]]

Before a goal is adopted, estimate what mapping it would take: how much evidence would have to exist, how many interviews, how long before the first branch could be acted on. Put that estimate next to the same estimate for the goal actually wanted. The operator then chooses with the gap in front of them, rather than discovering months later that they chose the cheap one without noticing there was a choice.

The point is not to make the expensive goal affordable. It is to make the moment of substitution visible, since that moment currently leaves no trace at all.

**Compared to the alternatives.** Acts before the drift rather than after, which is the only way to catch a substitution that has no symptom. It also produces a number the operator can revisit as circumstances change. Against filing the real goal as the root, it does nothing once the choice is made — the cheap goal, once adopted, is the root again and the estimate is history. The two compose well: cost first, then file honestly.

**What would make this the wrong pick.** Charting cost is genuinely hard to estimate in advance, and a bad estimate is worse than none, because it will be wrong in the direction that justifies whatever was already wanted. There is no obvious way to calibrate it before the fact.

Choosing or changing the outcome is a human's decision. This is a proposal about how that choice could be made, not a licence for any pass to make it.

## Definition of done

[[Estimate charting cost for three past goals and check the estimates against what happened]]

```
npx vitest run test/cli/chart-cost-estimate.test.ts
```

Green means: the estimate exists *before* the goal is committed rather than reconstructed afterwards — setting an outcome records a dated charting-cost figure, and the rollup reports estimate against actual per goal. That ordering is the whole solution: an estimate written after the choice cannot make the substitution a decision. Green does **not** say the estimates were any good; that retrospective judgement stays with a human.
