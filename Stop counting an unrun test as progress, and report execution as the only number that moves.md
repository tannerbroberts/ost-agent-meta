---
type: Solution
created: '2026-08-05'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Honest accounting is worth having even though it builds nothing and moves no test]]

**The mechanism: change the accounting, build nothing.** The rollup currently reports `built X%` from how many solutions carry a runnable command, which makes a day of instrumenting look like a day of progress. Stop doing that. Report readiness as readiness, keep `tested` where it is, and put the number that has never moved at the top rather than at the end of each line — so the tree states its own condition plainly instead of showing motion in the one dimension that is free.

**Why this shape.** It is the only candidate that makes no claim about how the situation should be fixed, which is appropriate given that the fix is a human's decision about their own hours. It just refuses to let the artifact flatter the work. The tree's own rollup already says `tested 0` on all thirty-four buckets; the problem is that it says it quietly, in a position that reads as a footnote next to a percentage that moves.

**Compared to its siblings.** The only one with no downside risk — no runner that could launder an exit code into a verdict, no ration that could withhold useful work. It is also the only one that changes nothing about the world: after it ships, exactly as many tests have been run as before, and the operator has a more honest dashboard describing the same stall. The other two are attempts to fix the problem; this is an attempt to stop hiding it, and it is worth being clear that those are different ambitions.

**What would make this the wrong pick.** If it is chosen *instead of* one of the others rather than alongside. A tree that reports its stall accurately and then does nothing about it for another 255 tests has converted a hidden problem into a well-documented one, and the operator whose hours do not exist is no better off. Its honest role is as a companion to whichever mechanism gets built, not as the answer.

⚠️ Unvalidated. Agent-ideated on 2026-08-05.

## Definition of done

[[Check the rollup reports readiness and execution as separate numbers, with neither called built]]

`npx vitest run test/ost/rollup-execution-first.test.ts`

No rollup line expresses instrument coverage as a `built` percentage, every bucket's executed count sits at least as prominently as its readiness count, and both numbers survive — readiness must not be dropped to achieve it. Red against today's output, which reads `built 13% (3/24 runnable), tested 0` on the buckets: a moving percentage for readiness and a trailing zero for the thing that has never happened.

## History
- 2026-08-05 unlinked [[Check the rollup reports readiness and execution as separate numbers, with neither called built]] — moved under [[Honest accounting is worth having even though it builds nothing and moves no test]] — the belief this test measures now has a node of its own
