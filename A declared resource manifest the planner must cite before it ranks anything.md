---
type: Solution
status: unvalidated
source: 'agent-ideated:2026-08-02-maintenance-pass-3'
created: '2026-08-02'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Hand-fill the manifest and count how many of the top five priorities move]]

The operator declares the project's resources once, as structured fields the tooling reads — capital and its deployment deadline, human hours and appetite, social reach (whether this operator will contact strangers at all), compute economics and the token-reset schedule, and which credentials will and will not be handed to an unattended run. The planner may not emit a priority order without naming which declared resources conditioned it, so an unstated assumption about the operator becomes a visible blank rather than a silent default.

**Mechanism:** declaration. The operator states what they know; nothing is inferred.

**What it would have changed here:** the cold-offer test was sequenced RUN FIRST on 2026-07-24 and killed on 2026-07-25 with "that isn't going to fly" — a declared social-reach field would have removed it from the candidate set before a pass spent a day drafting outreach.

**Blind spots, stated so the comparison is honest:** it only holds facts the operator thinks to declare, and it decays silently — a seed round closes, an appetite shifts, and the manifest keeps asserting last month's world with full confidence. It also front-loads cost onto the first five minutes of a stranger's use, which is the moment this product can least afford to spend.

**Compare against** [[Constraint profile mined from what actually blocked the loop]] (which pays nothing up front but learns only the expensive way) **and** [[Expiring resource questions asked at a fixed cadence]] (which fixes the staleness this one has but spends the scarcest declared resource, human minutes).

## Test

[[Hand-fill the manifest and count how many of the top five priorities move]]

`npx vitest run test/product/manifest-ranking-shift.test.ts`

Green when ranking the tree with a hand-filled manifest fixture moves a measurable share of the top five against ranking it without. It shows the planner is sensitive to declared resources; it does not show the new order is better, and it says nothing about whether an operator would keep a manifest true — a stale manifest the planner must cite is worse than none.
