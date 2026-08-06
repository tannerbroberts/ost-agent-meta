---
type: Solution
source: 'agent-ideation:2026-08-06-unattended-sweep'
created: '2026-08-06'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[The tools this product controls account for a minority of the path failures observed]]

**The idea.** Let the wrong guess happen, and make the first failure carry what the run needed. A missing path answers with the nearest existing ancestor and its contents; a permission denial says the path exists and the grant does not; a `git` call outside a repository says which directories above it are repositories. One turn is spent, and it returns the layout instead of a negation.

**Why this shape.** Every entry in the parent's census is a failure that told the run nothing it could act on. `sed: src/cli/index.ts: No such file or directory` leaves the run knowing one path is wrong and every other path equally uncertain, which is why the transcripts show the same shape recurring within a single session. The information that would have ended it — what *is* at `src/`, or that `src/` does not exist either — is sitting in the failing call's own stack frame and is discarded.

**How it differs from its siblings.** Both siblings try to prevent the wrong guess, and both must know something in advance to do it: the manifest must have anticipated the path, the observation rule must have made the run look at the right place. This one requires no foreknowledge at all, which makes it the only one that helps when the run's belief is wrong in a way nobody predicted. It is also the only one that adds no refusal, no bookkeeping, and no startup cost — it is strictly an improvement to a message.

**Why it may be the right one to build first despite being the least ambitious.** It degrades gracefully. If it helps less than hoped, the cost was a better error message; if either sibling is wrong, the cost is a mechanism that fights the run on every call. Against an opportunity whose evidence is entirely this agent's own transcripts and where no external operator has asked for anything, the cheapest reversible move has an argument its siblings do not.

**Where it fails, stated so it can be judged.** It concedes the turn — the run still pays for the wrong guess, it just gets more back. For a run being billed per turn under a spend ceiling, one informative failure per wrong belief may still be the dominant cost, and the parent's whole complaint is that turns are being spent. It also cannot help where the failure surface is not the product's to change: `sed` and `git` are not this repository's, so the improvement covers only the calls that pass through its own tools.

**Cost.** Error-path changes at each of the product's own tools. No new state.

⚠️ Unvalidated. Agent-ideated from the agent's own transcripts — usability evidence, not evidence that anyone wants this.
