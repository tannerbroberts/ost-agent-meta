---
type: Solution
source: 'agent-run:unattended-sweep-2026-08-27'
created: '2026-08-27'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[Displaying an item is a sufficient signal to advance the window, with no disposition state at all]]

**Variation dimension: automated-vs-manual. Position taken: automate the selection completely; leave the disposition entirely manual.**

Stamp each member of each capped queue with the firing that last displayed it, and sort every capped list by that stamp ascending — never shown first, then longest-unshown. The stamp is written by the act of returning the item, so it needs no judgement, no agreement about what "handled" means, and no new tool. A second firing is shown members the first was not, mechanically, whether or not anybody did anything about the first 25.

**Why this line is drawn here and not further along.** The tempting adjacent move is to automate disposition too — let a pass mark an item settled and drop it from the queue. This candidate refuses that on purpose. Deciding that a correctly-declined instrument, or a piece of evidence that only corroborates an existing node, is *finished* is a judgement about the tree's content, and the sibling needs under this parent record what happens when passes make it silently. Display order is bookkeeping and is safe to automate; disposition is a claim and is not. So the queue never shrinks under this candidate — it only rotates.

**What it gives up, stated plainly.** Recency of display is not recency of attention. An item shown to a firing that ignored it is stamped as freshly seen and sinks to the bottom of the order exactly as if it had been read carefully, so a genuinely urgent item can rotate out for as many passes as a settled one. And because nothing ever leaves, the steady state is a slow carousel over a monotonically growing set: with 419 evidence items and 25 shown, full coverage takes seventeen firings, and it takes longer every week new evidence arrives. This candidate guarantees that everything is eventually seen and guarantees nothing about how soon.

**Cheapest form.** A `lastShownAt` (or last-firing-id) field in the vault's existing `.ost-agent/` sidecar, written when a list is served, read as the sort key where the ascending title/id sort is applied today in `src/mcp/next-work.ts`. No change to the `shown`/`total`/`hidden` contract, which already reports the denominator correctly; only the selection changes, which is the half the existing honesty fix did not touch.

Ideated by an unattended pass on 2026-08-27 against the assigned dimension. Not blind: this surface holds no grant to run independent parallel ideators, so all three candidates under this opportunity were composed in one context by one author, which is the condition the blind-ideation rule exists to prevent. Read the three as one author's three answers, and discount their apparent distinctness accordingly.
