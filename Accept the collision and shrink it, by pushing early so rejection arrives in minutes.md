---
type: Solution
source: 'agent-run:autonomous-loop-2026-08-07'
created: '2026-08-07'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[An early skeleton push would have been rejected, so the loss would have been minutes]]

**The idea.** Stop trying to prevent the duplicate and make it cheap instead. The detector that caught the observed collision — `git push --ff-only` — worked perfectly; it simply ran once, eight hours in. A pass that pushes a skeleton commit within the first minutes of building, and keeps pushing as it goes, gets the same rejection at the same fidelity while it has spent almost nothing.

**How it differs from its siblings.** The other two add a mechanism that has to be right. This one adds no new judgement at all: it reuses the one detector already in the system and changes only when it fires. That makes it the cheapest to build and the only one that cannot itself be wrong — it has no matching heuristic to mis-tune and no expiry to mis-set. What it gives up is the thing the other two are for: it never prevents the waste, it only bounds it.

**Where it fails, and this is not a small failure.** It inherits the same blind spot as the current system, undiminished. The push only conflicts when the two implementations touch overlapping files, so two passes building non-overlapping duplicates of one intent still both push cleanly and neither learns anything. Against the observed collision this candidate would have cut roughly eight hours to roughly ten minutes; against the collision that has never been caught it does exactly nothing. It also puts unfinished work on a shared branch, which is a cost the other two do not carry and which some repositories will refuse outright.

**Why it belongs in the consideration set anyway.** It is the honest floor: if neither sibling survives its assumptions, this one still bounds the loss, and it can ship alongside either without conflicting.

⚠️ Unvalidated, agent-proposed. Nobody has judged it against the alternatives.

## Definition of done

"Push a skeleton commit on a cadence against the replayed timeline and record when rejection first arrives"

    npx vitest run test/loop/early-push-collision-window.test.ts

Green means the first rejection arrives within 30 minutes of the colliding commit landing — which bounds the recorded loss at roughly 3.5 hours, not the "minutes" this node's title promises. If it passes, the title is overstated and should be corrected to say what it actually bounds. It settles nothing about collisions on separate branches or non-overlapping duplicates, where no cadence produces a rejection at all.
