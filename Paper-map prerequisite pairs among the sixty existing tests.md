---
type: AssumptionTest
status: unvalidated
evidence: assertion
source: 'INBOX:2026-07-24-external-review-five-dimension.md'
created: '2026-07-25'
---
#AssumptionTest #unvalidated #evidence/assertion

**Assumption (desirability):** real test sets contain enough genuine dependencies to be worth a schema and validator change.

**Method:** human with a printout of all 60 AssumptionTest titles marks genuine A-blocks-B pairs (B is unrunnable or uninterpretable until A lands). A few hours, zero build.

**Pre-committed threshold:** >= 10 genuine prerequisite pairs among the current 60, else the schema change dies here.

**Decides:** prerequisite edges vs a simple rank/route view (sibling 'Rank every node by how many blocked tests one build would unblock').

*Proposed by the agent-side hard-fix pass — to be run by a human. No results recorded here.*

## History
- 2026-07-24 evidence: (none) → assertion — labeled at creation intent; ost_create_node@0.1.3 silently dropped the evidence input
