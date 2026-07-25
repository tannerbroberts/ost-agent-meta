---
type: Solution
status: unvalidated
source: 'agent-ideation:autonomous-loop-2026-07-25-pass5'
created: '2026-07-25'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Do named unfixed thresholds actually get fixed]]

**The idea.** `ost-agent debt` (and `status`) name every assumption test whose
pre-commitment reads as an instruction rather than a commitment — no number, no
bound, opening on *Fix…* / *Decide…* / *Choose…* — and total them. Report only.
Nothing is blocked, nothing is refused, nothing is rewritten.

**Approach.** The extractor already returns the paragraph. This adds one shallow
classification on top of it, in the same spirit as the rest of the coverage feature:
it never asks whether the threshold is *good*, only whether it is a threshold.

**How it differs from its siblings.** [[Refuse to record a result against a threshold that was never fixed]]
enforces; [[Make the threshold a field the node carries, not a sentence in its prose]]
restructures. This one only looks. It is deliberately the weakest of the three, and
it is proposed first for that reason: the parent opportunity's own caveat is that a
mechanical rule here will be wrong at the edges, and a report that is wrong is a
nuisance while a refusal that is wrong is a wall.

**Size:** an afternoon. One function, two counters, two lines of output — the same
shape as the v0.9.0 increment that produced the finding.

**Trade-off.** A report nobody reads changes nothing, and this tree already has one
unrun assumption test about exactly that failure mode
([[Does the side-by-side change what a reviewer does about a threshold]]). Building
two reports before learning whether the first one is read would be a pattern worth
naming out loud.

**Cheapest disconfirmer.** [[Do named unfixed thresholds actually get fixed]] — name
them once, wait, and count how many are still unfixed.

⚠️ Unvalidated. Proposed by an agent from a mechanical census of its own two vaults.
