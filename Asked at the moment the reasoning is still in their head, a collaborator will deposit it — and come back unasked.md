---
type: Assumption
status: unvalidated
source: >-
  tree-restructure:2026-08-05 — the belief this solution's test was already
  measuring
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion
[[Offer the deposit prompt and count who comes back a second time unasked]]

One question in a surface they already use is the cheapest possible ask. The real test is not the first deposit, which politeness can produce, but a second one nobody prompted — that is the difference between a channel and a favour.

## 2026-09-08 — the channel this belief predicts has been open for 49 days and holds nothing

Kept short. A first-party measurement, not a census, and it bears on the ask rather than on the answer.

**What was measured.** Every evidence record in this vault, read off disk: **766 records** spanning 2026-07-22 to 2026-09-08. **Zero carry `actor: deposit`.** A search for `^actor: (deposit|retrospective|friction|slack|atlassian|actions|human|founder)` over `.ost-agent/evidence/` returns nothing at all, and the whole corpus is `transcript`, `inbox` or `usage`. The channel is not switched off: this firing's own `ost_ingest_inbox` reports `[deposit] 0 new` alongside `[atlassian] disabled — turned off in ost.config.yaml`, so open-and-empty is distinguishable from disabled in that output, and deposit is in the first state.

**Why this lands here rather than on the solution above it.** This node's second sentence is its sharp one — "the real test is not the first deposit, which politeness can produce, but a second one nobody prompted." After 49 days there is no first deposit to be unsure about. Whatever the unprompted-second rate turns out to be, it is multiplying a first-deposit count of zero.

**What this does NOT establish, which is the half that decides what to do next.** Zero records is equally consistent with two opposite stories and the vault cannot separate them: the prompt was offered and declined every time (declining stores nothing, by design), or it was never offered. One structural fact leans toward the second — `ost_deposit` is withheld on the unattended surface, so the surface that fires most often here cannot ask at all, and only an attended session can. If the ask has never been made, this belief has not been tested, and its child test would be measuring a delivery failure rather than a collaborator's willingness. Those want different fixes.

**The cheapest thing that would separate them, and it is not a study.** Record the offer, not only the answer. A count of times the prompt was put, beside the count of deposits stored, turns "zero" into either "asked 40 times, stored 0" — which refutes this belief hard and cheaply — or "asked 0 times", which retires the question until the ask exists. Nothing today records the offer, so the distinction is currently unobservable rather than merely unobserved.

**Limits.** This counts records on disk, not asks. The `actor` field is the predicate, so a deposit filed under some other actor would be missed — though no actor outside {transcript, inbox, usage} appears anywhere in the corpus. Whether attended sessions offered the prompt is not observable from the vault and was not checked elsewhere. The 766 figure counts files in `.ost-agent/evidence/`, a different denominator from the 653 unmapped the sweep reports; the two should not be differenced. Nothing was executed, no rung moved, no status changed, no node created, and `ost_check` is withheld on this surface, so this write is unverified by the invariant checker by design.

_Method: `Glob` and `Grep` over this vault's own `.ost-agent/evidence/`, plus this firing's own `ost_ingest_inbox` channel report. Observed structure of this vault, read first-party; it grounds the ask's delivery, not anyone's willingness._
