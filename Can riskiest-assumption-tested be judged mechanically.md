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
