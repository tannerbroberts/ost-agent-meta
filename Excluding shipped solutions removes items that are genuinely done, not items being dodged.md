---
type: Assumption
created: '2026-08-06'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Audit every shipped solution against the repository before trusting the exclusion]]

Feasibility, with a safety edge. The rule is only sound if `shipped` means built. The field is settable by an agent, and an agent that wants a queue shorter has an obvious move available — so the question is not whether the exclusion works mechanically but whether the population it removes is actually built. If any solution currently marked shipped is not, this rule hides it permanently from the one queue that would have chased it.
