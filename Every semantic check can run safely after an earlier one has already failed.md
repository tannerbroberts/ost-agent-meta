---
type: Assumption
source: 'agent-ideation:2026-08-30-unattended-sweep'
created: '2026-08-30'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion
[[A call carrying three semantic defects is refused once, naming all three, with no check throwing]]

**The belief, stated so it could be false:** the semantic checks are independent enough that each can run on input an earlier check already rejected, without throwing on garbage and without depending on a normalisation an earlier check performed.

**Why it could be false.** Short-circuiting on the first `throw` is not only a reporting choice — it is also a guard. A check that parses an instrument may assume the threshold check already established the node is an AssumptionTest; a check that inspects a lane may assume the title resolved to a node that exists. Accumulation removes that ordering guarantee from every check at once. If even a few of them are order-dependent, converting the layer turns clean refusals into crashes, and a crash on a malformed call is strictly worse than a serialised refusal: the caller learns nothing at all.

**Risk category:** feasibility.

**What would make it cheap or expensive.** Cheap if the checks are already written as independent predicates over the raw arguments. Expensive if any of them mutate shared state or rely on a prior check's coercion — that is per-check work spread across the whole layer, and it is the cost this candidate's own prose admits to.
