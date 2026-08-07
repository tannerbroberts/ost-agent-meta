---
type: Assumption
created: '2026-08-07'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Push a skeleton commit on a cadence against the replayed timeline and record when rejection first arrives]]

**The belief, stated so it could be false.** `git push --ff-only` rejects on divergent history, not on semantic overlap. The rejection at 08:47Z happened because the other session's commit was already on the branch — so any push after 02:56Z would have been rejected too, regardless of what it contained. On that reading the belief holds trivially and the candidate works.

It could be false in the direction that matters. The second pass started at 00:47Z, over two hours before the other commit existed. A skeleton push in the first ten minutes would have succeeded, told the pass nothing, and the pass would have continued. For this candidate to bound the loss, pushes have to continue *throughout* the build, and each one has to be cheap enough that a pass will actually do it — which is a claim about the loop's discipline, not about git.

The second way it fails is the one this candidate never escapes: rejection requires divergent history on the same branch. Two passes on separate branches, or building non-overlapping duplicates of one intent, produce no rejection at any cadence. This assumption covers only the shape of collision that has actually been caught.

⚠️ Unvalidated, agent-authored, and reasoning from a single recorded collision.
