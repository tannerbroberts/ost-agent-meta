---
type: AssumptionTest
status: unvalidated
source: 'INBOX:2026-07-24-external-review-five-dimension.md'
created: '2026-07-25'
evidence: assertion
instrument: npx vitest run test/ost/evidence-acknowledge.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Assumption (usability, with a harm check):** an acknowledge-with-reason affordance will not become a confabulation loophole in reverse — the agent lazily acknowledging evidence that contains a real need.

**Method:** a pass proposes acknowledge-or-map dispositions with reasons for the 7 consumed-but-uncited inbox items in this vault; the human blind-reviews each call without seeing the agent's reasons first. One sitting.

**Pre-committed threshold:** zero false acknowledgements (no item containing a real need waved through); at most 1 over-mapping tolerated. Any false acknowledge kills the affordance in favor of the standing false-alarm ledger.

**Decides:** ship the affordance vs keep the permanent-false-alarm status quo vs the Context node type.

*Proposed by the agent-side hard-fix pass — to be run by a human. No results recorded here.*

## History
- 2026-07-24 evidence: (none) → assertion — labeled at creation intent; ost_create_node@0.1.3 silently dropped the evidence input
- 2026-08-05 instrument: (none) → npx vitest run test/ost/evidence-acknowledge.test.ts — There are no acknowledge calls to blind-review, because no acknowledge verb exists — the stranded count went from seven to eighteen this pass for exactly that reason, and every one of the eighteen turned out to be already cited in an existing Opportunity body. This asserts the verb the review presupposes: acknowledging an evidence item records a reason and the node it was filed under, removes it from `unmappedEvidence`, and is refused without a reason, so an acknowledgement can never be a silent dismissal. Missing-spec red, not assertion red — the verb does not exist, so the command fails on a missing file; a builder should write it against the real sweep so it goes red on an item that stays listed after being acknowledged. It does not settle the test's own question, which is whether the calls a pass makes are honest filing or avoidance — that is a blind human review and stays with a human.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/ost/evidence-acknowledge.test.ts` — No test files found, exiting with code 1
- 2026-08-22 **green** (exit 0) `npx vitest run test/ost/evidence-acknowledge.test.ts` — Duration  3.27s (transform 171ms, setup 0ms, collect 257ms, tests 2.79s, environment 0ms, prepare 34ms)
