---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

Every ask a run cannot answer itself goes into one durable queue, aged, with the command that would clear it. The operator visits when they choose, works down the list, and each thing they clear releases whatever was behind it. Nothing chases them and nothing is lost.

Age is what makes the queue useful rather than a second inbox. An ask that has been outstanding for eleven days is a different object from one filed an hour ago, and only the queue can tell the operator that — the run that filed it was gone before the eleven days elapsed.

**Compared to the alternatives.** The only option that survives across runs, which matters because the same ask will otherwise be raised fresh by every pass that hits it. It respects the operator's attention rather than interrupting it, and it accumulates the picture that a per-run notification cannot. The price is latency by design: a queue visited weekly means a week of blocked work, and nothing about the mechanism resists that.

**What would make this the wrong pick.** Queues that are never emptied become furniture. If the ask rate exceeds the visit rate for long, the queue turns into a monument to blocked work, and the operator gets a large number where they used to get a small surprise.
