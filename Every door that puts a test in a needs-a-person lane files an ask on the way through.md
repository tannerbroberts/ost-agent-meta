---
type: Solution
source: 'agent-ideation:2026-09-01-unattended-sweep'
created: '2026-09-01'
evidence: assertion
killIf: >-
  A humans-required test created after this ships still shows `ageDays: null` in
  `outstandingAsks` thirty days later.
killBy: '2026-12-01'
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[The creation-time humansRequired argument is what put all 62 ageless entries in the queue]]

**Variation dimension: when-it-acts — at what moment the clock starts. Position taken: at write time, at the single door, and nothing retroactive.**

There are two ways a test reaches a lane compute may not run. `flagHumansRequired` and `setLane` both file an ask through `appendAsk`, so tests arriving that way carry a date. Creation with `humansRequired:` sets the lane and files nothing. This candidate closes the second door by routing it through the same call as the first: setting a needs-a-person lane and filing an ask become one operation that cannot be half-performed.

**Why this position and not another.** The parent node's mechanism section shows `pendingAskQueue` deriving *membership* from two conditions and *age* from one. That asymmetry is the bug, and it is cheapest to fix where the asymmetry is created rather than where it is observed. Every downstream reader — the CLI queue, `outstandingAsks`, the sort comparator — then works unmodified, because they were all written correctly against a ledger that was simply never populated by this path.

**What it deliberately gives up, plainly.** It does nothing at all for the 62 entries that already exist. Those tests are already born; there is no moment left to stamp them, so on the day this ships the operator's queue looks exactly as it does now and stays that way until the population turns over. If the tree's tests are long-lived — and 62 entries predating ask tracking suggests they are — this candidate's benefit arrives on a timescale measured in however long it takes to write 62 new tests. The sibling that derives an age from `## History` is the only one of the three that helps today.

**What would make this the wrong pick.** If the creation-time door turns out *not* to be how the 62 arrived — the parent node flags this as inferred rather than read — then this fixes a path nothing uses and the real writer is somewhere else. That is why the test beneath it is aimed at the inference and not at the repair.

**Honest note on how this was ideated.** All three candidates under this opportunity were composed in one context by one author. This surface holds no grant to run independent parallel ideators, so discount their apparent distinctness accordingly.

Unvalidated. Agent-ideated 2026-09-01; a human to review.

## Definition of done

"A test born humans-required arrives in the ask queue already carrying a date"

```
npx vitest run test/ost/pending-ask-queue.test.ts -t "a test born humans-required at creation is in the queue with a non-null age"
```

**What that command settles, and what it does not.** It settles feasibility: whether the creation path can be made to file an ask, and whether the queue then reports a real age instead of `null`. It settles nothing about desirability — a dated ask is not an answered ask, and whether the operator's answering rate moves at all is a separate belief that no exit code reaches.

**Honest note on the strength of this red.** `test/ost/pending-ask-queue.test.ts` exists and its describe blocks are real, so this is not a bare missing file. But the `-t` filter names an assertion nobody has written, so today it fails with "no test found matching" — which is one step above `no-spec` and still short of a genuine assertion failure. The deliverable is the failing assertion, not the filter: a builder should add a case to the existing `an ask raised mid-pass survives into later runs` describe that creates the test through the `humansRequired` argument rather than through `flagHumansRequired`, then asserts `ageDays` is a number. That case will go red against today's code for this question specifically, and green when the door is closed.
