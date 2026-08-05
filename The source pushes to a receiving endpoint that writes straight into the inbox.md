---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[The operator's real experiment sources can push anywhere at all]]

A small authenticated endpoint accepts posted results and files them as evidence records. Systems that already emit webhooks on completion point at it. Data arrives when the experiment finishes rather than when someone next runs a sweep, and nobody carries anything.

**Compared to the alternatives.** The only option of the three with no latency — evidence lands at the moment it exists, which matters when a result is what unblocks a decision. It also needs no per-source code, since the source already knows how to send. Its weakness is reach: it works only for sources that push, which excludes most spreadsheets, most survey tools' free tiers, and anything a human runs by hand. A pull adapter covers those and this cannot.

**What would make this the wrong pick.** It puts a listening service in the loop, with the reachability, authentication, and replay problems that come with one — and a missed delivery is invisible, where a failed pull is at least a channel reporting that it could not read. For a single-operator vault on a laptop, that may be more surface than the latency is worth.

## History
- 2026-08-05 unlinked [[Count how many of the operator's real experiment sources can push anywhere at all]] — moved under [[The operator's real experiment sources can push anywhere at all]] — the belief this test measures now has a node of its own
