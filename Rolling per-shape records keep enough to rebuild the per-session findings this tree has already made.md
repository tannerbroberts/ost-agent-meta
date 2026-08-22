---
type: Assumption
source: 'agent-ideation:2026-08-21-unattended-sweep'
created: '2026-08-22'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Replay all 4 named per-session findings against rolling records and require every one to be reproducible]]

**Feasibility belief, and the one that decides whether this candidate can ship at all:** a rolling per-shape record can carry enough that every finding this tree has already drawn from per-session records could still have been drawn.

The bar is not "keeps some data". It is that the specific analyses already in the vault survive. Four of them, named so this is checkable rather than a hope:

- **"83 across 28 sessions"** — needs occurrence and distinct-session counts. A counter carries this.
- **"the worst sessions burned 9, 8, 7, 6, 6, 6 and 5 calls"** — needs the per-session *distribution*, not a total. A counter loses it.
- **"eight consecutive denials in one firing, on 2026-08-17T07:16Z"** — needs a single session isolable by id and timestamp, which is precisely what stops existing when records are keyed by shape.
- **"two captures contain a byte-identical failing command twenty-six hours apart, in two sessions with no memory of each other"** — needs two individually addressable sessions and their times.

Two of the four survive a counter and two do not, so the belief as stated is already in trouble on inspection. What would rescue it is a rolling record that keeps a per-session series rather than a scalar — at which point the honest question is whether that is meaningfully different from keeping the 385 files somewhere the queue does not look, which is a different and simpler candidate than this one.

If the belief is false, this candidate is not merely worse than its siblings — it is actively destructive, because it would delete the raw material of the tree's best-evidenced nodes in exchange for a shorter queue.
