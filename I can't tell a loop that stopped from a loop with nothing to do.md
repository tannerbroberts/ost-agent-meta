---
type: Opportunity
source: 'USAGE:2026-09-03'
created: '2026-09-07'
evidence: assertion
authorship: machine
---
#Opportunity #unvalidated #evidence/assertion
[[A dead-man's-switch outside the host, because an in-host watchdog dies with the host]]
[[The sweep response states when the loop last fired, computed from the trace already on disk]]

**The need, in the operator's voice:** "My loop is configured to fire every hour. It produced nothing for three days. Every surface I read — the sweep, the rollup, the buckets — looked exactly as it always does, and not one of them told me the thing had stopped."

## What was observed, first-party, on 2026-09-07

Three independent artifacts inside this vault agree that **no firing occurred on 2026-09-04, 2026-09-05 or 2026-09-06**, against a configured `loop.cadence` of `1h`:

- **The tool-invocation trace.** `.ost-agent/usage/events.jsonl` carries 109 events stamped 2026-09-07 and **zero** stamped 09-04, 09-05 or 09-06.
- **The usage evidence records.** Every record from 2026-08-23 through 2026-09-02 was minted the next day, between 00:00 and 03:47. Then the pattern breaks: `USAGE_2026-09-03.md` carries `fetchedAt: 2026-09-07T14:02:02Z` — four days late — and no record exists for 09-04, 09-05 or 09-06 at all.
- **Node creation stamps.** Node frontmatter carries `created:` dates on 09-01, 09-02 and 09-03, and none on 09-04, 09-05 or 09-06.

**And nothing reported it.** This firing's own `ost_next_work` returned its buckets in the ordinary shape, and the rollup described the tree's contents accurately. Both are computed from what is *in* the tree. Neither is a function of whether the loop that fills the tree is alive, so a dark loop and a busy one produce the same report.

## Why this is a need and not a preference

The mandate this whole tree serves is to "observe its own runs, name where it failed itself, and patch that failure — reliably, unattended". Three days of not running is the largest possible gap in that loop, and it is the one condition the product's own reporting cannot express. An operator budgeting compute against these reports would have read three days of silence as three days of nothing needing attention.

## Litmus test (more than one way to address this?)

Yes, and they are genuinely different: state the age of the last firing in the sweep response; keep a firings ledger and compare observed cadence against the configured one; hang a dead-man's-switch outside the host, since an in-host watchdog is down whenever the host is; push a notification on a gap rather than waiting to be read. Passes.

## Why this is not the sibling beside it

The nearest neighbour is "A run that dies while I am away stays dead, and nothing says where it stopped", and Torres's test separates them in both directions:

- "Resumable append-only process journal" fully serves that node — the next pass can see where a dead run stopped — and does **nothing** here, because there is no run to resume. Zero runs leave zero journal.
- An age-of-last-firing line in the report fully serves this node and does **nothing** for that one, because a run that started and died on schedule has a perfectly recent firing stamp.

That node is *a run stopped mid-work and left no marker*. This node is *no run started, and no surface says so*. Different failures, different repairs, different owners.

## Limits, and the most important one is that the cause is unknown

This establishes that no firing happened; it does **not** establish why. The host may have been off, the spend ceiling may have been exhausted, cron may have been disabled, or a lock may have been held. The gap is also weekend-shaped — 09-04 was a Friday, with Saturday and Sunday following — so a closed laptop is a live and mundane explanation.

That does not weaken the need; it *is* the need. An operator cannot currently distinguish a crash from a closed laptop from a quiet week, because the product reports the tree's contents and never its own liveness. Whether the outage was benign is exactly the question no surface here can answer.

Further limits: the three signals are all internal to this vault, so a firing that ran and wrote absolutely nothing would be invisible to all three alike and would be miscounted as an outage. Nothing was executed. The 109-event and zero-event counts are exact greps over `events.jsonl`; the minting pattern is read from eleven `fetchedAt` stamps.

**Provenance and rung.** Machine-recorded trace plus node frontmatter, read first-party. Recorded at `assertion` rather than `observed`: the finding is an inference from *absence* across three artifacts rather than a recording of an event, and no external party has corroborated it. A human may judge it worth promoting.

Unvalidated. Mapped by an unattended sweep on 2026-09-07; a human to review.
