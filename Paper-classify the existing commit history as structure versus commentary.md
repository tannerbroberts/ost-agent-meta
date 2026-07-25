---
type: AssumptionTest
status: unvalidated
evidence: assertion
source: 'INBOX:2026-07-24-external-review-five-dimension.md'
created: '2026-07-25'
---
#AssumptionTest #unvalidated #evidence/assertion

**Assumption (feasibility):** commentary-vs-structure is reliably detectable from commit contents alone.

**Method:** hand-label this vault's full commit history (structure = new nodes/links/status; commentary = annotations/appends only); apply the proposed classifier rule on paper to the same commits. Hours, existing data.

**Pre-committed threshold:** >= 90% agreement between rule and hand labels, else the idle-down trigger cannot be trusted and the solution is deferred.

**Decides:** build idle-down vs rely on the mark-acknowledged affordance to make done-ness reachable.

*Proposed by the agent-side hard-fix pass — to be run by a human. No results recorded here.*

## History
- 2026-07-24 evidence: (none) → assertion — labeled at creation intent; ost_create_node@0.1.3 silently dropped the evidence input
