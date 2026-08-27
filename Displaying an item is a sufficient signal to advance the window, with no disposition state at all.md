---
type: Assumption
source: 'agent-run:unattended-sweep-2026-08-27'
created: '2026-08-27'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion

**The belief, stated so it could be false.** Sorting by "when was this last shown to a firing" is enough on its own to make a second firing see members the first was not — without anyone deciding what counts as handled, and without any item ever leaving the queue.

**Risk category: feasibility.** It is a claim about whether the mechanism works, not about whether anyone wants it.

**How it could turn out false.** The stamp is written when a list is *served*, and a list is served every time `ost_next_work` is called. A single firing calls it repeatedly — the maintenance loop is explicitly "re-call `ost_ingest_inbox`, then `ost_next_work`, and repeat" — so within one pass the first call stamps the head, the second call is shown the next 25, the third the next, and by the end of a long pass the ordering has churned through a large slice of the queue without any of it being worked. The next firing then starts wherever the previous one's last confirmation call happened to leave off, which is not the same as "where the previous firing stopped paying attention". If that is how it behaves, the mechanism advances the window faster than it advances the reading, and the guarantee it was bought for — everything is eventually *seen* — degrades into everything is eventually *scrolled past*.

**What settles it.** Two calls that differ only in being the second, over a queue larger than the cap, must return disjoint or near-disjoint members; and the stamp must distinguish a firing from a call, or the paragraph above is what happens.

**What a green here would still leave open.** Nothing about whether rotation is the right policy, and nothing about whether an operator would rather choose the slice themselves. Feasibility only.
