---
type: AssumptionTest
status: unvalidated
source: 'agent:P4_assumptions'
created: '2026-07-24'
---
#AssumptionTest #unvalidated #usability

**Assumption under test (usability, with desirability implications):** Seeing an evidence class on a node changes what a reader is willing to act on, rather than becoming a badge they scroll past.

**Proposed test:** Show five people the same branch twice — once plain, once with evidence classes on every node. Ask each time: "which part of this would you commit a week of work to, and why?" Compare answers and reasons.

**Size:** an afternoon; needs only rendered mock-ups, no implementation.

**Pre-committed threshold:** ≥4 of 5 identify the weakest-evidence node in the labelled version AND at least 3 change their stated next action between versions. If the answers are identical, the labels cost writing effort and buy nothing.

**Decides:** whether per-node labelling is worth the friction it adds to every write, versus branch-level propagation.

Proposed by the agent — to be run by a human with real readers. No results recorded here.
