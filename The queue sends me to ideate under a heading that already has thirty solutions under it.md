---
type: Opportunity
source: 'TRANSCRIPT:49d6b2d3-b867-4996-9d9d-8f10dd0871de'
created: '2026-08-07'
evidence: observed
---
#Opportunity #unvalidated #evidence/observed

The tree files its needs in two tiers. A small set of category opportunities sit directly under the Outcome — "Tools fail", "The run stalls on me" — and the specific needs hang beneath them. That shape is enforced, and it is the right shape: it is what makes a thousand-node tree readable.

The work queue does not know about it. `underservedOpportunities` counts a node's *direct* solution children and reports anything under three. A category opportunity is never supposed to have direct solutions — its job is to hold sub-opportunities — so every well-formed category reads as maximally under-served, permanently, no matter how much work sits beneath it.

The effect is not a cosmetic miscount. It is an instruction to do the wrong work. A pass that takes the queue at its word ideates three solutions directly under a heading whose subtree already holds thirty, and those three can only restate what is already there, because they are addressing the same need one level up. The tree gets more overlap, the category still reads as under-served on the next pass, and the overlap is now permanent.

## What was observed

On 2026-08-07 an unattended pass was handed 24 under-served opportunities. Cross-checking each against the tree's own rollup: "Trust an unmonitored agent enough to walk away" was reported as having 0 solutions while carrying 10 opportunities, 31 solutions and 33 tests beneath it. "I can't leave the process running unattended without worrying" was reported as 0 while carrying 37 solutions. "The agent has to guess what resources it's actually working with" was reported as 0 while carrying 45. Taking the queue literally would have added roughly 72 solutions, essentially all of them redundant.

## What would settle it

Whether the count should roll up through sub-opportunities, or whether category nodes should simply be exempt from the under-served check, is a design question and a human's to answer. What is not in question is that a node with 45 solutions beneath it should not be reported as needing three.

## History

- 2026-08-07 — Created from a first-party observation during an unattended maintenance pass, by comparing the pass's own `underservedOpportunities` list against the rollup counts printed at the head of the same pass.
