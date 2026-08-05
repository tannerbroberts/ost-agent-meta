---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: At most 2 in 10 aged-out items are judged to have mattered.
instrument: npx vitest run test/ost/backlog-ageing-rule.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that ageing sorts by actionability rather than by difficulty. Ageing rewards neglect: the surest way out of the outstanding list becomes being ignored, and the items most likely to be ignored are the hard ones — so the backlog it assembles may be exactly the work that most needed attention.

**Risk category: feasibility.**

**Design.** Reconstruct the sweep as it stood at several past points and apply a candidate ageing rule — say, five consecutive passes untouched. List what would have moved to the backlog. Then a person marks each as genuinely unactionable or as something that mattered and was being avoided.

**Why it is small.** The history supports reconstruction, and the rule is a counter.

**What it will not cover.** Marking an item as having been avoided is a judgement made by the person who avoided it. A second reader would strengthen this considerably and is worth the extra hour.

A human runs this and records the result.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/ost/backlog-ageing-rule.test.ts — Applies the ageing rule to the recorded sweeps and asserts the items it would have moved are counted and still recoverable rather than dropped; fails today because there is no backlog for anything to age into.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/ost/backlog-ageing-rule.test.ts` — No test files found, exiting with code 1
