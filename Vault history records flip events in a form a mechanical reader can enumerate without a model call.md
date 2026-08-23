---
type: Assumption
source: 'INBOX:2026-08-11-observed-build-loop-reports-not-merged-on-merged-prs.md'
created: '2026-08-23'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[A digest built from a fixture vault names every seeded red-to-green flip and nothing else in its top three]]

**Feasibility.** This solution's whole premise is that "nothing new is measured" — a distiller reads what is already on disk. That premise rests on a belief nobody has written down: that the events worth surfacing are recorded in a shape a mechanical reader can *enumerate*, not merely a shape a human can recognise on re-reading.

**Stated so it could be false.** A red-to-green flip may exist in vault history only as free prose inside a node's `## Instrument Log` or `## History` — lines whose wording has drifted across versions of the writer that produced them. If so, no enumerator can list the flips without a model reading every node, the digest stops being a distillation of records and becomes a fresh model pass over the whole vault every firing, and this candidate loses the cost advantage that distinguishes it from its siblings.

**Why it is worth writing rather than assuming.** The solution's only other belief, "What the founder means by highlights is already present in vault history", is about *whether the right events are recorded*. This one is about *whether recorded events can be got back out*. Both can fail independently: history could hold exactly the right twenty flips and still yield them to nothing but a model, and it could be trivially enumerable while listing the wrong things. A digest needs both to be true, and only one of them was on the tree.

**What this pass could and could not establish.** First-party `ost_read_repo` of this product's own source: `src/eval/` already computes rollups, coverage and build permits over node bodies, so machinery for reading the vault structurally exists, and `## Instrument Log` is a reserved section no tool may author or rewrite — which is exactly the property that makes it a candidate record to enumerate. What this pass did **not** establish, and what the test beneath this node is for, is whether those log lines are uniform enough that a flip can be recognised from the line alone. Nothing was executed; the modules were read, not run.

**Provenance caveat.** Agent-origin, from a read of this repository. Grounds feasibility only, and is silent on desirability — it says nothing about whether anyone wants the digest.
