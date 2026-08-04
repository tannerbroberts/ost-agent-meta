---
type: AssumptionTest
status: unvalidated
created: '2026-08-02'
evidence: assertion
threshold: >-
  Keeps at least four of the five records judged to carry a product need, and
  drops at least twenty of the twenty-four judged not to.
instrument: npx vitest run test/telemetry/friction-surface-rule.test.ts
---
#AssumptionTest #feasibility #unvalidated #evidence/assertion

**The assumption under test (feasibility):** that filtering by which tool failed separates signal from noise well enough to be worth adopting. This pass produced an unusually clean subject: 29 records, each read in full, with an explicit judgement of which five carried a product need.

**How it would run:** apply the rule to all 29 and compare its keeps and drops against that judgement, item by item.

**The disagreement to look for specifically:** the rule is expected to drop the shell-quoting and blocked-sleep records, and two of the five mapped needs were distilled from exactly those. If it does, the rule is precise and blind in the same stroke, and the honest reading of a "passing" score would still be that it discards the channel's most useful pattern. That outcome should be recorded as a caveat rather than a pass, and the comparison against the recurrence rule is the decision this feeds.

Retrospective, no build required — the records and the judgement both already exist. Proposed by the agent; a human runs it and records the outcome.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/telemetry/friction-surface-rule.test.ts — Runs all 29 recorded friction records through the surface rule and asserts it keeps the ones touching the product's own surface and counts the rest; fails today because every record is filed alike.
