---
type: AssumptionTest
status: unvalidated
source: 'agent:P4_assumptions'
created: '2026-07-24'
---
#AssumptionTest #unvalidated #feasibility

**Assumption under test (feasibility):** "Has this solution's riskiest assumption been tested?" can be decided by a rule, consistently enough to gate real work without becoming arbitrary.

**Proposed test:** Write the candidate rule. Apply it to all 24 solutions now in this tree. Separately, have a human judge each one by hand without seeing the rule's verdict. Compare.

**Size:** an hour of rule-writing plus an hour of human judgement, against data that already exists.

**Pre-committed threshold:** ≥80% agreement overall AND no disagreement on any solution the human marks "clearly not ready." A gate that waves through obviously unready work is worse than none, because it launders the decision.

**Decides:** whether the gate can be automatic, advisory, or must stay a human call.

Proposed by the agent — the hand judgement must be human and blind to the rule's output. No results recorded here.
