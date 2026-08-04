---
type: AssumptionTest
source: 'TRANSCRIPT:e335a680-ee48-4171-b8ad-4cfb526e4129'
created: '2026-08-04'
evidence: assertion
threshold: >-
  Classifying every TS2552/TS2339-shaped failure in the captured transcript
  corpus, at least 3 in 10 are dropped-intention (the symbol was never defined
  anywhere in the session) rather than wrong-name (a near-match existed at the
  time of the call).
instrument: npx vitest run test/telemetry/symbol-failure-census.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Category: viability — of building this at all.** The solution above admits its own weakness: it does nothing for the misspelling case. So the decision is not "does it work" but "is there enough of the case it covers to be worth the mechanism". This test is the census that answers that, and it is deliberately placed to be able to kill its own parent.

**Lane: compute-only.** The corpus is the transcript records already captured in this vault, and the classification rule is mechanical: a failure is dropped-intention when the named symbol appears nowhere in the session's final source state, and wrong-name when a near-match existed at the moment of the call. No judgement call is left to a person.

**Pre-committed, including the losing branch.** Below 3 in 10, this solution should be set `deferred` and the effort should go to the two siblings, which cover the misspelling case between them. Writing that down before the count is the point — the two captures currently on the record split one each way, which is a sample of two and predicts nothing.

**What a green run does NOT settle.** It establishes that the case exists at a rate worth addressing. It does not show the ledger would be used — this option depends on the run volunteering a declaration, and every mechanism that relies on the agent remembering an extra step deserves scepticism the census cannot supply. It also says nothing about whether a run *notices* the end-of-batch report of still-open intentions.

## Definition of done

`npx vitest run test/telemetry/symbol-failure-census.test.ts`

Red today: no census exists and the classifier it needs is unwritten.

## Instrument Log
- 2026-08-04 **red** (exit 1) `npx vitest run test/telemetry/symbol-failure-census.test.ts` — filter:  test/telemetry/symbol-failure-census.test.ts
