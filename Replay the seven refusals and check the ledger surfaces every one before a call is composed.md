---
type: AssumptionTest
created: '2026-08-05'
evidence: assertion
threshold: >-
  All seven observed refusal classes are present in the ledger exactly once
  each, with their permitted form, and all seven are surfaced to a session
  before it composes its first call.
instrument: npx vitest run test/loop/corrections-ledger.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**The assumption: a correction can be stored in a form a later session actually receives.** Not that it will be obeyed — that a durable record can be built from a refusal without a person writing it, and delivered before the reflex fires rather than after.

**Risk category: feasibility.**

**Design.** Replay the seven machine-captured sessions' refusals through the ledger writer. Assert the ledger holds each distinct refusal class exactly once — deduplicated, since seven copies of the same correction is the failure it was built to fix, one level up — each carrying the permitted form the guard named. Then start a session against that ledger and assert all seven reach it before its first composed call.

**Why it is small.** The corpus already exists on disk and the refusal messages already contain the permitted form. Nothing needs to be run live.

**What it does NOT cover, and it is most of what matters.** Whether a session that receives the correction acts on it. The node's own weakness is that a reflex which survived seven explicit refusals may well survive a note about them, and this test cannot see that — it proves delivery, not persuasion. It also cannot see the unbounded-growth failure, which only appears after months of refusals.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/loop/corrections-ledger.test.ts` — No test files found, exiting with code 1
