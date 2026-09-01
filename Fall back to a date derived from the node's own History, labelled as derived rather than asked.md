---
type: Solution
source: 'agent-ideation:2026-09-01-unattended-sweep'
created: '2026-09-01'
evidence: assertion
killIf: >-
  A human reads twenty derived dates against the git history of the same nodes
  and more than four are wrong by over a week.
killBy: '2026-12-01'
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[A date reconstructed from History is close enough to when someone was actually asked to be worth ordering by]]

**Variation dimension: what-is-given-up — precision versus coverage. Position taken: give up exactness to cover the population that already exists.**

Do not wait for new tests to be born correctly. When `latestAsk` returns nothing, read the date off the artifact the node already carries: every lane-setting write files a dated `## History` line, and node creation is itself dated. Report that as the age, in a field that says plainly it was derived and not asked — a third state alongside "asked N days ago" and "never asked", so nothing is passed off as a record that is actually a reconstruction.

**Why this position and not another.** The sibling that fixes the door is correct and helps nobody this quarter, because it cannot reach back. This is the only one of the three that puts a number against all 62 entries on the day it ships, and 62 entries is the entire current population — the problem is retrospective by construction, so a repair that only works forwards leaves the observed instance untouched.

**The labelling is load-bearing, not decoration.** `src/knowledge/asks.ts` is explicit that `null` must stay distinguishable from "asked just now" because *"zero would read as fresh"*. A derived date has exactly the same hazard one level up: silently presenting a reconstruction as a filing would mean the ledger's own guarantee — that an ask's date is when somebody actually asked — stops holding, and no reader could tell which entries still honour it. So the third state is the price of doing this at all.

**What it deliberately gives up, plainly.** Accuracy it cannot check. A `## History` line records when the lane was set, which is not necessarily when anybody was asked — a test relabelled during a cleanup pass would date from the cleanup, not from when the operator first owed an answer. So the derived ages will be wrong in a direction that flatters: they will make old asks look younger than they are. That is the failure this node's kill criterion goes looking for.

**What would make this the wrong pick.** If the derived dates cluster — if most of the 62 were labelled in a handful of bulk passes — then the ordering they produce is nearly as flat as the one they replace, and the work bought a field rather than a signal.

**Honest note on how this was ideated.** All three candidates under this opportunity were composed in one context by one author; this surface holds no grant to run independent parallel ideators. Discount their apparent distinctness accordingly.

Unvalidated. Agent-ideated 2026-09-01; a human to review.

## Definition of done

"An entry with no ledger record still reports an age, and says where that age came from"

```
npx vitest run test/ost/pending-ask-queue.test.ts -t "an entry with no ask on the ledger reports an age derived from History, marked derived"
```

**What that command settles, and what it does not.** It settles feasibility and the labelling invariant: that a derived age appears, and that it is distinguishable from a filed one. It cannot settle whether the derived dates are *right* — that needs a person comparing them against git history, which is this node's kill criterion and not its instrument.

**Honest note on the strength of this red.** The spec file exists; the assertion does not, so today the command fails with "no test found matching" rather than on an assertion. A builder's deliverable is the case, not the filter: seed a vault whose test carries a `## History` lane line and no ask ledger entry, then assert the queue entry reports a non-null age together with the marker saying it was derived.
