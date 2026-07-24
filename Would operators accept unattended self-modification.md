---
type: AssumptionTest
status: unvalidated
source: 'agent:P4_assumptions'
created: '2026-07-24'
---
#AssumptionTest #unvalidated #desirability

**Assumption under test (desirability):** Operators will accept a system that changes its own workflow while running, given rollback — rather than demanding to approve every change.

**Proposed test:** Describe the mechanism to five prospective operators — scheduled swap at a checkpoint, automatic rollback on a bad version — and ask what they would insist on approving beforehand and what would make them turn it off entirely.

**Size:** five short conversations against a written description; nothing built.

**Pre-committed threshold:** ≥3 of 5 accept unattended swapping with rollback and no prior approval. If most demand approval, this option collapses into its sibling (propose-for-one-click-adoption) and should not be built separately.

**Ethical/harm check to include:** ask explicitly what a self-modifying system could do that they would consider unacceptable, and record the answers verbatim.

Proposed by the agent — to be run by a human with real operators. No results recorded here.
