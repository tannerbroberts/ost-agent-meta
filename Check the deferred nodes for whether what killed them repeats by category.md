---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  At least 15 abandoned solutions exist, and the top 3 causes account for half
  of them.
instrument: npx vitest run test/ost/deferred-cause-recurrence.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that failure repeats by category — that a vault which has abandoned three ideas on the same viability question will keep meeting that question. If each death is idiosyncratic, history supplies no prior and this route has nothing to work from.

**Risk category: feasibility.**

**Design.** Take every deferred or abandoned solution in this vault and both its siblings. Read what killed each. Group the causes and count. A concentrated distribution supports the approach; a flat one, where every death has its own reason, refutes it.

**Why it is small.** The record exists. The work is reading it and tallying.

**What it will not cover.** This vault is young and has abandoned few ideas — one node is currently retired. If the sample is too small to show a distribution, that is the finding, and it also means the approach would not work here yet regardless of whether the assumption is true in general.

## History
- 2026-08-05 instrument: (none) → npx vitest run test/ost/deferred-cause-recurrence.test.ts — Both clauses of the threshold are counts over what the vault already records — "at least 15 abandoned solutions exist, and the top 3 causes account for half of them" — so the tally needs no person. The spec walks every node with status `deferred` across this vault and its siblings, reads the cause out of the History line that recorded the transition, groups the causes, and asserts both the sample size and the concentration of the top three. It fails today for the reason the node itself predicts and would rather find out cheaply: nothing groups deferral causes, and the vault currently has one retired node against a required fifteen, so the sample-size clause fails outright. That is a real red rather than a missing-file red — the assertion goes against today's data and would keep failing until the vault has actually abandoned enough ideas to have a distribution. This settles whether history supplies a usable prior in THIS vault; it says nothing about whether failure repeats by category in general, which is the broader claim the solution leans on.
