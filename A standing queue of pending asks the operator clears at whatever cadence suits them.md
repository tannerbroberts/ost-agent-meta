---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[An operator will actually visit a queue that never chases them]]
[[Every ask in the standing queue carries the date it was asked, whichever surface filed it]]

Every ask a run cannot answer itself goes into one durable queue, aged, with the command that would clear it. The operator visits when they choose, works down the list, and each thing they clear releases whatever was behind it. Nothing chases them and nothing is lost.

Age is what makes the queue useful rather than a second inbox. An ask that has been outstanding for eleven days is a different object from one filed an hour ago, and only the queue can tell the operator that — the run that filed it was gone before the eleven days elapsed.

**Compared to the alternatives.** The only option that survives across runs, which matters because the same ask will otherwise be raised fresh by every pass that hits it. It respects the operator's attention rather than interrupting it, and it accumulates the picture that a per-run notification cannot. The price is latency by design: a queue visited weekly means a week of blocked work, and nothing about the mechanism resists that.

**What would make this the wrong pick.** Queues that are never emptied become furniture. If the ask rate exceeds the visit rate for long, the queue turns into a monument to blocked work, and the operator gets a large number where they used to get a small surprise.

## Definition of done

"Build the queue from asks already outstanding and see whether the operator empties it once"

`npx vitest run test/ost/pending-ask-queue.test.ts`

The spec asserts the two properties that separate this node from what already ships: an ask raised mid-pass by one run is still in the queue on a later run, and it carries a non-null age plus the command that would clear it. Age is what the node says makes this a queue rather than a second inbox, so it is the right thing to make falsifiable.

**This one is red against today's code, not merely against a missing file.** `ost_next_work` already returns `outstandingAsks`, aged — but it is derived only from `blockedOnPermission` tests, so an ask a run could not answer itself is never persisted and the field reports `ageDays: null`. The spec fails on today's behaviour, which is a better definition of done than "create this file."

**What a green here does not settle.** Whether the operator ever empties it. The node's own stated failure mode is that queues nobody visits become furniture — a monument to blocked work — and a passing spec proves only that the monument would be accurately dated.

## History
- 2026-08-05 unlinked "Build the queue from asks already outstanding and see whether the operator empties it once" — moved under "An operator will actually visit a queue that never chases them" — the belief this test measures now has a node of its own

## The queue shipped, and the age it was built for is null on every real entry (unattended sweep, 2026-08-28)

Two corrections to the Definition of done above, both from first-party `ost_read_repo` reads this pass.

**The spec named above is no longer red.** `test/ost/pending-ask-queue.test.ts` now exists and is written in full. It asserts exactly the two properties this node claims: an ask filed mid-pass by `flagHumansRequired` survives into a later run with `askedAt` at T0 and `ageDays` of 11, and it carries the clearing command. It also pins the clearing rule (recording a result drops the entry) and the deliberate exclusion (an unlabelled test is triage backlog, not an ask). So the paragraph above beginning "This one is red against today's code" describes a state that has passed; the mechanism shipped. Left in place rather than rewritten, because it is the accurate record of why the spec was written.

**The gap moved rather than closed, and this is the part worth a builder's attention.** In production this pass's `ost_next_work` reports 52 outstanding asks, of which 52 have `askedAt: null`. Every single one. The queue this node argued for is fifty-two entries deep and not one of them has the age the node calls its whole point — which is the "monument to blocked work" this node's own failure-mode paragraph predicted, arriving through a route it did not predict.

The reason, read off the code: `src/ost/pending-asks.ts` admits an entry when the lane says a person is what it waits on OR an ask is on the ledger, but takes `askedAt` from the ledger alone. `src/ost/lanes.ts` files an ask from the lane-*setting* path. A test that is born humans-required — `humansRequired` passed to `ost_create_node` — enters through the lane branch and never touches the ledger. And the surface that creates such tests in volume, the unattended pass, is precisely the one where `ost_flag_humans_required` is withheld: the path that files asks is closed to the actor that generates them.

## Definition of done — dated entries from every filing surface

"A test created humans-required files an ask, so its queue entry has an age from the first pass that sees it"

`npx vitest run test/ost/ask-filed-at-creation.test.ts`

That spec does not exist yet, so today the command fails as `no-spec` and mints no build permit — an honest limit, stated rather than glossed. The assertions it must carry are written out in full on the test node, and they are predicted to fail against `src/ost/pending-asks.ts` as it stands. The pass that specified this could read the repository but not write to it.

_First-party observation of the repository and of this pass's own sweep response. Grounds feasibility, not demand. No test was run and no result is recorded._
