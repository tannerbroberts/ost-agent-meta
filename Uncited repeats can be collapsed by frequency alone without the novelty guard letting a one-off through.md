---
type: Assumption
source: 'agent-ideation:2026-08-30-unattended-sweep'
created: '2026-08-30'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion
[[Twenty old records sharing one uncited signature collapse, while the equally old novel singleton stays listed]]

**The belief, stated so it could be false.** Redundancy can be established by a signature repeating inside the evidence store, with no node citing it, and the existing novelty guard still spares an item that occurs once.

This is the load-bearing belief of the candidate above, and it is a feasibility question about code rather than a question about anyone's wants. It could straightforwardly turn out false in either direction:

- **False the dangerous way.** Frequency-based redundancy buries a novel item. The current predicate leans on a human having cited the signature, which is a weak but real proxy for "someone judged this worth keeping." Swap that for a raw count and the thing protecting a one-off is only the count itself — so a genuinely new problem that happens to fire three times in one session could collapse on its first appearance. That is precisely the failure the existing spec's header calls out in capitals, and the reason this belief must be tested against the guard rather than beside it.
- **False the harmless way.** The queue's records turn out not to share signatures with each other at all — each self-manufactured record differing in some volatile field, each real error carrying a unique path or id — in which case widening the predicate collapses nothing and the whole candidate is inert.

**Risk category: feasibility.** Nothing here is about demand. Whether an operator wants a shorter queue is a separate belief and is not what this measures.

**Why the repository can settle it and no person needs to.** The mechanism, the fixture, and the novelty guard all already exist in `test/evidence/age-out-preserves-novel.test.ts`, which builds twenty-one records on one identical timestamp so that pure age cannot pass. Extending that fixture to a signature no node cites is a small change to a spec that is already written, and the exit code is the answer. Spending a person's afternoon on a question whose answer is on disk would be spending the scarcest thing in this process on something that was never about customers.

Unvalidated. Agent-ideated 2026-08-30.
