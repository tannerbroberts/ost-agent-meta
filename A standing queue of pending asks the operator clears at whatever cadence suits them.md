---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[An operator will actually visit a queue that never chases them]]

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
