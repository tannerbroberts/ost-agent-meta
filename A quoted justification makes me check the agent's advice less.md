---
type: Opportunity
source: >-
  agent-observation:autonomous-loop-2026-07-26-tenth-pass — the prose-lane
  reader quoting a split declaration back as a clean one
created: '2026-07-26'
evidence: assertion
---
#Opportunity #evidence/assertion
[[Every machine-selected quote carries the sentence it was cut from]]
[[Refuse to recommend when the source does not read cleanly]]
[[Mark what the machine chose differently from what a human wrote]]

**The need, stated as an operator would.** *When the agent shows me its evidence, I read the quote and stop checking. I need to know when the quote is the part that is wrong.*

**What produced this.** `ost-agent lanes` printed a paste-ready command to classify an assumption test into the lane an unattended pass may run, and offered the test's own sentence as the reason. The sentence was real, correctly transcribed, and from the right node. It was also cut in half: the test read *"Lane: compute-only for the census, humans-required for the fixing"*, and the recommendation quoted only as far as `compute-only`. Pasting it would have moved the human half of a split test into compute's reach — using the test's own words as the argument for doing so.

**Why this is a need and not just a bug.** The bug is fixed (v0.16.0 refuses a declaration that names two lanes). The need it exposes is structural and survives the fix: **this product's whole safety argument is that a human makes every permissive call, and a human making that call reads what the agent hands them.** A quote is the strongest signal of groundedness the interface has, so it is also the most efficient way to be confidently wrong. Every recommendation this product renders — the lane suggestions, the paste-ready verdict drafts in the docket, the hygiene findings — has the same shape: agent-selected excerpt, human decision, and no way for the human to see what was cut.

**Why it ladders to the outcome.** The outcome counts operators who return for a second pass on a real vault. An operator who pastes a recommendation and later discovers it was wrong in the direction of *more* automation does not come back — and this is precisely the class of error that a reviewer skims past, because it arrives wearing evidence.

**Litmus test — more than one way to address it?** Yes, several, and they disagree with each other: quote whole sentences rather than fragments; show the excerpt's surroundings so the reader sees what was elided; refuse to recommend when the source is ambiguous (what v0.16.0 did, for one detector); mark machine-selected excerpts distinctly from human-written ones; or drop paste-ready commands entirely and make the operator open the node. Which is right is not obvious.

**Provenance and confidence.** Agent self-observation during the tenth autonomous pass, on this product's own vault. Rung `assertion` — nobody outside this building has met this interface, and no operator has been observed trusting or distrusting a quote. That is the same floor as almost everything else in this tree, and it is worth stating plainly that the party reporting *the agent's advice can mislead* is the agent.
