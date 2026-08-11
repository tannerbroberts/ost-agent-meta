---
type: AssumptionTest
source: 'agent-ideated:2026-08-02-unattended-sweep-priority-order'
created: '2026-08-02'
evidence: assertion
threshold: >-
  At least 3 of 5 readers name a specific row they would move AND quote that
  row's stated reason as what they disagree with. Fewer than 2 doing so kills
  the candidate.
instrument: npx vitest run test/ost/ranked-ledger-reasons.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**The assumption under test (usability / value):** that a reason printed beside a rank is *challengeable*, not decorative. The whole defence of an authored ledger is that an operator can disagree with a sentence in a way they cannot disagree with a silence. If readers skim the reasons and accept the order anyway, the mechanism has bought fluent self-justification at the price of a per-row authoring cost every pass, and should not be built.

**The test:** hand a reader a ten-row slice of this vault's priority order with a written reason beside each row, and ask one question — which row is in the wrong place, and what in its reason is wrong? Say nothing about wanting disagreement. Five readers, each seeing the list cold, no discussion between them.

**Pre-committed before running, so this can come out a failure:** at least three of the five must name a specific row they would move *and* quote that row's stated reason as the thing they disagree with. A reader who moves a row on a hunch without engaging the reason does not count — that is the null result this test exists to detect. Two or fewer readers engaging a reason kills the candidate.

**What it deliberately does not cover:** whether the order was any good. This measures only whether stated reasons are load-bearing for a reader, and a list can pass this bar while being wrong in every position. It also says nothing about the authoring cost holding up across 324 rows rather than ten.

**Note on who can run it:** the measurement is what people say when handed a list, so it cannot be run by compute. The lane label is a human's to set.

## History
- 2026-08-05 instrument: (none) → npx vitest run test/ost/ranked-ledger-reasons.test.ts — Asserts the refusal that is this node's entire mechanism: a ledger row whose reason is missing, empty, or cites no node title or evidence id is refused a rank and lands in the named unranked tail rather than a confident position. Red today because no ranked ledger and no write-boundary refusal exist.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/ost/ranked-ledger-reasons.test.ts` — No test files found, exiting with code 1
- 2026-08-11 **green** (exit 0) `npx vitest run test/ost/ranked-ledger-reasons.test.ts` — Duration  314ms (transform 68ms, setup 0ms, collect 101ms, tests 23ms, environment 0ms, prepare 32ms)
