---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: At least 6 of 10 have a check expressible without a model's judgement.
instrument: npx vitest run test/ost/regretted-write-invariants.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that regretted writes are mostly mechanically detectable — that for a typical bad write there exists a check, expressible over the call's arguments and the tree's state, which would have refused it. If most regrets turn on judgement instead, the refusal set cannot grow to meet them.

**Risk category: feasibility.**

**Design.** Collect the last ten writes a human considered mistakes, from the annotations and history already in the vault. For each, write down the check that would have caught it, and mark whether that check is expressible over information available at call time without a model's opinion.

**Why it is small.** The material already exists in the vault, and the output is ten yes-or-no judgements with the proposed check written next to each.

**What it will not cover.** It looks only at regrets that were noticed and recorded. Bad writes nobody has spotted are absent from the sample by construction, and they may be exactly the kind no check would catch.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/ost/regretted-write-invariants.test.ts — The threshold — "at least 6 of 10 have a check expressible without a model's judgement" — becomes a property of committed code the moment the checks are written: the spec commits the ten regretted writes already recorded in this vault's annotations and history as fixtures, replays each against the pre-write invariant set, and asserts at least six are refused on information available at call time. It fails today because no pre-write invariant set exists and no regretted write is committed as a fixture.

## Instrument Log
- 2026-08-06 **red** (exit 1) `npx vitest run test/ost/regretted-write-invariants.test.ts` — No test files found, exiting with code 1
