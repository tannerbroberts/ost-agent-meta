---
type: Assumption
source: 'agent-ideation:2026-10-17-unattended-sweep'
created: '2026-10-17'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion

**Risk category: usability.**

**The belief, stated so it could be false:** when a record says `retry ×8 (8 reused an id already seen)`, the person or pass reading it discounts those eight and does not go looking for a problem.

**How it could be false.** Readers skim the kind and the count and never reach the parenthesis. Or they read it and do not know what a reused id means, so they treat it as one more detail. Either way the label exists and changes nothing, and this candidate is strictly worse than the siblings, which act on the reader's behalf.

**Why no spec can settle it.** A spec can show the label is emitted correctly. Whether anyone acts on it is a fact about readers, not code. Emitting the label is the easy half and is not where this candidate's risk lies.
