---
type: Opportunity
source: >-
  observation:src/knowledge/asks.ts + src/ost/pending-asks.ts + ost_next_work
  outstandingAsks 62/62 askedAt:null (2026-09-01)
created: '2026-09-01'
evidence: assertion
authorship: machine
---
#Opportunity #unvalidated #evidence/assertion
[[Every door that puts a test in a needs-a-person lane files an ask on the way through]]
[[Fall back to a date derived from the node's own History, labelled as derived rather than asked]]
[[Order the queue by what answering would unblock, and drop age as the ranking key]]

**Customer need (operator's perspective):** "Sixty-two things are waiting on me. Not one of them tells me how long it has been waiting, so they all look equally urgent, which means they all look equally ignorable. I open the list and close it again."

## The mechanism, read off the source rather than inferred

`src/knowledge/asks.ts` opens by stating what the ask ledger is for: *"when the tree asked the sponsor for something, so silence has an age."* It names the failure it was built to close — P2 — in its own words: an agent "could not tell a signature asked for yesterday from one asked for 40 days ago. Both looked like `lane: pending-permission`, which reads as the system working."

That failure is currently live for the entire population, by a route the module does not anticipate.

- `pendingAskQueue` (`src/ost/pending-asks.ts`) derives membership from two independent conditions: `waitsOnPerson` — the test carries a lane compute may not run — **or** an ask exists on the ledger.
- It derives `askedAt` and `ageDays` from **only one** of them: `latestAsk(ledger, t.title)`. When no ledger record exists, both are `null`.
- The ledger is written by `appendAsk`, which `src/ost/lanes.ts` calls from the lane-filing path (`flagHumansRequired`, `setLane`).

So a test that reaches a needs-a-person lane by *being born there* — the `humansRequired:` argument on node creation — satisfies the membership condition and misses the timestamping one. It joins the queue permanently ageless.

**The observed consequence, from this pass's own sweep:** `outstandingAsks` holds 62 entries and the summary states *"62 predate ask tracking and have no recorded age."* Every single one. The queue's sort is `(b.ageDays ?? -1) - (a.ageDays ?? -1)`, whose entire purpose is oldest-first, so with a uniformly-null population the ordering degenerates to tree order — and the module's own comment says why that matters: *"the longest-unanswered ask is the one the operator is most likely to have forgotten, so it leads even on a capped display."* Nothing leads. The display is capped at 25 of 62, ordered by nothing.

## Why this is a third instance of a pattern the parent node already named

The parent records, of the authorship field: *"An attribute that is constant across the corpus cannot contribute to any ordering built on it."* It reached that about `unvalidated` (universal status) and about authorship (0 human-written of 1606). This is the same defect in a third field — and the sharpest of the three, because unlike the other two this field was **purpose-built to vary**. A status that is universally `unvalidated` is at least accurate. An age that is universally unknown is a mechanism reporting that it has never once fired.

## Litmus test (is there more than one way to address this?)

Yes, and they trade off against each other rather than being one fix described five ways:

- File an ask at creation time, so the door that sets a lane and the door that files an ask become the same door.
- Backfill the ledger from each node's `## History`, which already carries the dated line for when the lane was set.
- Fall back to the node's own creation date when no ask exists, and mark the age as derived rather than asked.
- Stop reporting a bare `null` and render "never asked" as its own visible class, so the gap is legible instead of blank.
- Leave ages alone and order the queue by something that does vary — the cost of answering, or what each answer would unblock.

The first four disagree about where the clock comes from; the last denies that a clock is the right ordering key at all. Passes.

## What this node deliberately does not claim

That the creation-time door is the one all 62 came through is **inferred, not read**. What was read first-party: that `askedAt` is sourced only from the ledger, that the ledger is written only by the lane-filing path, and that 62 of 62 entries carry no record. Confirming that `ost_create_node`'s `humansRequired:` argument writes a lane without filing an ask needs a look at the creation path in `src/security/tools.ts`, which this pass did not open — and one of the tests beneath this node is aimed exactly there, so the inference is falsifiable rather than assumed.

It also takes no view on whether the operator *would* answer a dated ask. This node is about the ordering signal being absent; whether a present signal changes behaviour is a separate belief, and "Route the humans-required solution into the ask queue instead of dropping it from the instrument queue" already carries a humans-required test on precisely that question. This node should not be read as evidence for it.

_Method: first-party `ost_read_repo` reads of `src/knowledge/asks.ts`, `src/ost/pending-asks.ts`, `src/ost/lanes.ts` and `test/ost/pending-ask-queue.test.ts` in full, plus this firing's own `ost_next_work` response. Nothing executed, no result recorded. Observed property of this product's own artifact — it grounds usability, not desirability, and is not evidence that anyone outside the building wants anything._
