---
type: AssumptionTest
status: unvalidated
source: 'agent:P4_assumptions'
created: '2026-07-24'
evidence: assertion
instrument: npx vitest run test/eval/riskiest-assumption-judge.test.ts
---
#AssumptionTest #unvalidated #feasibility #evidence/assertion

**Assumption under test (feasibility):** "Has this solution's riskiest assumption been tested?" can be decided by a rule, consistently enough to gate real work without becoming arbitrary.

**Proposed test:** Write the candidate rule. Apply it to all 24 solutions now in this tree. Separately, have a human judge each one by hand without seeing the rule's verdict. Compare.

**Size:** an hour of rule-writing plus an hour of human judgement, against data that already exists.

**Pre-committed threshold:** ≥80% agreement overall AND no disagreement on any solution the human marks "clearly not ready." A gate that waves through obviously unready work is worse than none, because it launders the decision.

**Decides:** whether the gate can be automatic, advisory, or must stay a human call.

Proposed by the agent — the hand judgement must be human and blind to the rule's output. No results recorded here.

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-04 instrument: (none) → npx vitest run test/eval/riskiest-assumption-judge.test.ts — Runs the judge over solutions whose riskiest assumption is labelled and asserts its pick agrees; fails today because no judge exists and no labelled set is committed to score against.
- 2026-08-04 instrument: npx vitest run test/eval/riskiest-assumption-judge.test.ts → npx vitest run test/ost/riskiest-assumption-judgement.test.ts — This test asks whether a mechanical judgement is possible at all, so a spec is the direct form of the question rather than a proxy for it — score the candidate rule against a fixture set of solutions whose riskiest assumption has been labelled in advance, and assert agreement above a committed bound; it fails today because no rule and no labelled fixture exist.
- 2026-08-04 instrument: npx vitest run test/ost/riskiest-assumption-judgement.test.ts → npx vitest run test/eval/riskiest-assumption-judge.test.ts — Restoring the instrument this test already carried; the preceding replacement in this History was made in error, from misreading the default `needsHumans` lane as an instrument gap.

## Instrument Log
- 2026-08-04 **red** (exit 1) `npx vitest run test/eval/riskiest-assumption-judge.test.ts` — No test files found, exiting with code 1
