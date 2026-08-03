---
type: Solution
source: 'agent-ideated:2026-08-03-unattended-sweep-unattended-decisions'
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Show the operator ten forks already taken and count the reversals and the minutes]]

**Where authority sits: taken by the run, returned at review.** The run does not stop and does not ask. It picks the fork, and in the same breath records three things: the assumption it proceeded under, what it would have done had the answer been otherwise, and what undoing this would cost now versus later. The human's job moves from answering questions to reviewing decisions already taken — and the reversal price is the number that tells them which ones to review first.

This is the candidate that leans on the substrate this product already has. Every write is append-only and auto-commits to git, so "revertible" is not a promise the mechanism has to invent — it is a property of the vault. That is what makes stating a reversal cost honest rather than rhetorical: for most decisions inside the vault the cost really is one revert.

**How it compares to its siblings.** It is the only candidate that gets a full unattended run out of a decision-heavy task, and the only one whose value does not depend on the human doing anything in advance. It is also the only one that can be wrong in a way the human never sees: the queue candidate fails loudly and the contract candidate fails by refusing, but this one fails by proceeding.

**Its chief risk, stated plainly because it is the objection this node exists to face.** The parent's body names it: an unattended run that takes the fork itself is how an agent quietly becomes the person deciding what the product is. This candidate does not dissolve that risk, it *prices* it — and the price is only real if someone pays it. If the review never happens, or happens as a rubber stamp over a list too long to read, then the mechanism has converted every fork into a decision the agent made and nobody ratified, while producing a paper record that looks like oversight. That is strictly worse than stopping, because it is deniable.

**The distinction that decides whether it is usable at all** is reversal cost, not confidence. A confidently-taken decision to publish a package is not recoverable by a revert; a hesitantly-taken decision about node placement is. Any version of this that keys off how sure the agent felt rather than how expensive the undo is has reinvented the failure it was built to avoid.
