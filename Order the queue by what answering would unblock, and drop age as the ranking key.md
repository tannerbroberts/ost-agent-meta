---
type: Solution
source: 'agent-ideation:2026-09-01-unattended-sweep'
created: '2026-09-01'
evidence: assertion
killIf: >-
  The computed leverage score is identical for more than three quarters of the
  queue, so the ordering it produces is as flat as the one it replaced.
killBy: '2026-12-01'
authorship: machine
---
#Solution #unvalidated #evidence/assertion

**Variation dimension: what-it-measures — which property decides the order. Position taken: not elapsed time at all, but consequence.**

Stop trying to date the asks. Rank each entry by what answering it would release: how many solutions sit above it with no other route to a result, whether it is the only test under its assumption, whether anything downstream declares it a prerequisite. Age becomes a displayed detail rather than the sort key, and the queue answers "which one buys the most" instead of "which one has been ignored longest".

**Why this position and not another.** Both siblings assume the operator's question is *how long has this waited*. That assumption deserves challenging. An ask can be old because it is unimportant, and thirty days of silence is at least as good evidence that nobody needs the answer as it is evidence of neglect — so an oldest-first queue actively promotes the entries the operator has already implicitly declined, twice a month, forever. Leverage has the opposite bias, and it is the ordering the parent branch already established as wanted: the sibling opportunity "Nothing names the one node to pick up next, so choosing is work before the work" and the operator's own recorded words — *"not just what is the highest leverage — but also, why"* — both point here rather than at a clock.

**It also sidesteps the defect entirely rather than repairing it.** Leverage is computed from tree structure, which is fully present for all 62 entries right now. No ledger, no backfill, no missing field: the input this ranking needs has never been the thing that was missing.

**What it deliberately gives up, plainly.** The thing the ask ledger was actually built for. `src/knowledge/asks.ts` names its purpose as making silence visible — *"so silence has an age"* — and P2 is a recorded commitment that an unanswered ask gets surfaced as unanswered. Ordering by leverage means a genuinely neglected ask that unblocks nothing sinks to the bottom permanently and is never surfaced by anything. That is not a side effect; it is this candidate declining a commitment the product already made, and whoever picks it should pick it knowing that.

**What would make this the wrong pick.** If the tree's structure is too uniform to score — most tests are the only test under their assumption, and almost nothing declares a prerequisite — then leverage is near-constant and this reproduces the exact failure it was built to escape, in a more expensive way. That risk is real enough on this tree to be the kill criterion.

**Honest note on how this was ideated.** All three candidates under this opportunity were composed in one context by one author; this surface holds no grant to run independent parallel ideators. Discount their apparent distinctness accordingly.

Unvalidated. Agent-ideated 2026-09-01; a human to review.

## Definition of done

"The queue's order changes when leverage changes, and does not change when only dates change"

```
npx vitest run test/ost/pending-ask-queue.test.ts -t "the queue orders by what answering would unblock, not by elapsed days"
```

**What that command settles, and what it does not.** It settles that the ordering is computed from structure and is insensitive to the ask dates — the mechanical half. It says nothing about whether the resulting order is one the operator agrees with, which is the whole question of whether this beats its siblings and is irreducibly a person's judgement.

**Honest note on the strength of this red.** The spec file exists and its `the operator's own surface reads the same queue` describe is the natural home, but this assertion is unwritten, so today the command fails on the filter rather than on an assertion. The deliverable is the case: build a fixture with two ageless entries where one is the sole test under an assumption carrying several solutions and the other unblocks nothing, then assert the first leads — and assert the order is unchanged when both are given contrasting `askedAt` values.
