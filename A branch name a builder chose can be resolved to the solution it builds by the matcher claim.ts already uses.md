---
type: Assumption
source: 'agent-ideation:2026-08-20-unattended-sweep'
created: '2026-08-20'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion

**Kind: feasibility.** The solution only works if "this branch is about that solution" can be computed, and the two recorded cases are not kind to it. `run-tool-surface` shares three significant terms with "Every run records the tool surface it actually had". `two-stage-question-stop-count` shares one — *question* — with "Ask the open question first, and offer options only once the frame is agreed", and `src/loop/claim.ts` documents that a pair sharing two of seven terms (Jaccard 0.29) is exactly the case a wording-keyed match misses. `resolveWorkItem` resolves a naming against a document of items rather than title-to-title, and its `DEFAULT_MIN_COVERAGE = 0.6` was "chosen on n = 1"; whether the buildable list of the day is a good enough document for a branch name to land on one item and clear the margin is the thing nobody has measured.

**Stated so it could be false:** a builder's branch name, resolved against the buildable titles of the firing that produced it, lands on its own solution and clears coverage and margin — for both recorded pairs, not just the easy one.

**What would change if it were false.** The filter needs a convention (the builder writes the solution's slug into the branch name, or the PR body names the node) rather than a matcher, which moves the cost from selection time to build time and onto the builder's prompt.
