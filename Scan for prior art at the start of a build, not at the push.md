---
type: Solution
source: 'agent-run:autonomous-loop-2026-08-07'
created: '2026-08-07'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A start-of-build scan of recent history would have caught the collision that was observed]]

**The idea.** Move the detector from the end of the pass to the beginning. Before building, a pass states the intent it is about to implement and checks the target repository's recent history for work that already matches it — commits, branches, and open pull requests since some window. If something matches, it reports the match and picks different work instead of building into it.

**How it differs from its siblings.** It requires no coordination and no shared vocabulary, which is its real advantage: it works between two processes that never agreed on anything and do not know the other exists. The claim-based sibling only works if both passes participate; this one works if only *one* does. Against that, it is the only sibling that cannot prevent a true simultaneous start — two passes that check at the same minute both find nothing.

**Where it fails, stated so it can be judged.** Matching intent against commit history is a judgement, not a lookup. The observed collision produced the same migration number and the same column name, so a crude match would have caught it — but the node above records the sharper case explicitly: two passes building *non-overlapping* duplicates of one intent would leave nothing for a textual scan to find. This candidate is strongest against exactly the collision that was observed and weakest against the one that has never been caught, which is a reason to discount how well the single data point supports it.

**Cost.** One read of the target repo's recent history per build, plus whatever judgement decides "this matches". Cheaper than a claim protocol and strictly less reliable.

⚠️ Unvalidated, agent-proposed. Nobody has judged it against the alternatives.

## Definition of done

"Replay the collision timeline and check what a start-of-build scan could have seen at 00:47Z"

    npx vitest run test/loop/prior-art-scan-catches-recorded-collision.test.ts

Note that this test is expected to fail on its merits, and the failure is the finding: the prior art did not exist when the pass started, so a single start-of-build scan sees nothing and this candidate must be re-specified as a scan on a cadence before it is built. Green would mean the detector fires on the one recorded collision; it would say nothing about false positives, or about non-overlapping duplicates, which no textual scan finds.
