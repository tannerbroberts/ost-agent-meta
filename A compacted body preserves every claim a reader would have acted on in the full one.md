---
type: Assumption
source: 'agent-ideation:2026-08-31-unattended-sweep'
created: '2026-09-01'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion
[[A person reads ten compacted bodies and marks every claim the full body made that the rendering dropped]]

**The belief, stated so it could be false:** a general-purpose compactor, given a node body it knows nothing about, produces a rendering that carries every claim a reader would have acted on — in particular the negations, the retractions and the limits, which are the sentences a summariser is most likely to drop and the most expensive to lose.

**Risk category: desirability**, in the sense that matters here — not whether anyone wants the feature, but whether the output is fit to decide from. It is the reason this candidate is cheap, and it is also the reason it may be unusable at any price.

**Why it might well be false, with instances from this tree.** The nodes this pass read are full of sentences whose entire value is a qualification: "the claim as written is false and here is the true form"; "5 of 6 sampled retry-sets were prescribed-only, not 4 of 4 with the rest inferred"; "this says nothing about the 44 entries this surface could not page to". A compactor optimising for the gist drops exactly these, and the resulting rendering reads more confident than the original — which is worse than reading less, because nothing in the output signals that a hedge was removed.

**The asymmetry that makes this sharp.** A lossy read is indistinguishable from a faithful one at the point of use. The failure produces no error, no flag and no friction event; it produces a pass acting confidently on a claim that was withdrawn three sections down. Every other candidate under this opportunity fails loudly by comparison — a suppressed append is a missing note, a mis-routed section is an absent block — and this one fails by being wrong quietly.

**What would make it true enough to use.** If reserved sections bypass compaction entirely and are served verbatim, the class of loss that revokes a human's finding is closed by construction, and what remains at risk is the agent's own reasoning. That is a much smaller stake and might be acceptable. Enforcing that exception against a component this project does not maintain is itself the open question.

Unvalidated. Agent-surfaced 2026-08-31.
