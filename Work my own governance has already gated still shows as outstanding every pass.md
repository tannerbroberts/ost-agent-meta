---
type: Opportunity
status: unvalidated
source: 'INBOX:2026-07-25-friction-ost-next-work-demands-solutions-under-7-opportun.md'
created: '2026-08-02'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion
[[Split the outstanding list by who may act on it, and report only this actor's share]]
[[An acknowledgement that records a decision not to act, and takes the item off the sweep]]
[[Items age out of the default view into a backlog that is counted but not reported]]

Some opportunities in a tree are deliberately held: they carry an evidence-debt or prioritization gate written into their own bodies, saying in effect "do not ideate here until X". The outstanding-work counter cannot read that governance, so it reports the same seven items as needing solutions on every run, forever.

That puts the operator between two bad outcomes. An obedient quota-filler trampled the gate it was told to respect; a governed pass reports identical outstanding work every time and never reaches done. Either way the counter has stopped being information — it is a standing demand that the tree's own rules forbid satisfying.

**The need:** I want the outstanding-work report to respect the holds I have already placed, so that what it lists is work I actually want done.

There is more than one way to address this: make the counter gate-aware and exclude held nodes, let a node declare a hold the tooling can read as a field rather than prose, report held items in a separate section that does not block done, or expire holds after a stated condition so they cannot become permanent silence.

## Provenance

Distilled from `INBOX:2026-07-25-friction-ost-next-work-demands-solutions-under-7-opportun.md` — filed by the twenty-passes ambient driver against 5 strategic opportunities and 2 dogfood needs carrying explicit gates.

## History
- 2026-08-02 evidence: stated → assertion — Demoted from 'stated' for consistency: rests on an inbox friction note, and the inbox channel's earned ceiling is 'assertion'.

## Issues
- 2026-08-02 Duplicate of a prior disposition — flagged by the pass that created it, 2026-08-02. The Outcome's ledger for the twenty-passes cycle 2 (2026-07-25) records "quota-vs-gate friction → MAPPED: appended to the same node (mechanism 3)", meaning this evidence is already carried on "The pass never says it is done, so I can't tell when to stop paying for compute" — which is this node's parent. So parent and child now represent the same evidence at two levels. This pass created the node because the append had left the item showing as unmapped. Worth a human's attention beyond the merge question: this node's subject is the governance gating that the same prioritization pass established, and a pass that cannot see those gates keeps being asked to fill quotas the gates forbid — which is what happened here.

## The same trap, now confirmed in a second bucket — 2026-08-05 unattended sweep

This node was written about `underservedOpportunities` re-demanding solutions under gated nodes. The identical failure has now been observed in `solutionsMissingInstruments`, and it is worth recording separately because the remedy a pass applied there was *designed* to clear the item and did not.

**Four of the 25 solutions this sweep was handed had already been dispositioned, in writing, by prior passes:**

- **"Refuse a wiki-link that contains a newline"** — the 2026-08-05 pass set `status: shipped` and wrote the reason into its History verbatim: it did so "because it was sitting in `solutionsMissingInstruments`, and a red-now instrument is impossible for behaviour that already ships." That was a remedy aimed squarely at this bucket. The node is `status: shipped` today and the bucket listed it again.
- **"A result must state what it did not cover"** — `status: shipped`, plus a 2026-08-04 `## Issues` note explaining at length why no instrument was written ("an instrument must be red when it is written, and this behaviour already ships"). Still listed.
- **"Append-only tool surface with no delete or shell tool"** — dispositioned twice, on 2026-08-04 and again on 2026-08-05, the second note ending "Two passes have now declined to make that call, which is itself worth knowing." Still listed. This sweep would have been the third.
- **"Post-session transcript harvester"** — a detailed 2026-08-05 note establishing the mechanism shipped and the residual test belongs to a person. Still listed.

**The mechanism is the same one established on "Evidence that fits no layer keeps coming back, so the pass never runs out of work", and generalises past evidence.** A pass's disposition is written where a *reader* looks — `## Issues`, `## History`, a status field — and the sweep computes its buckets from something else. There, mapping was readable only from frontmatter `source:`. Here, `status: shipped` is set, is correct, and is apparently not consulted by the instrument check either. In both cases the tree records the decision faithfully and the counter cannot see it.

**Why this costs more than the evidence case.** An unmapped evidence item is re-read. A dispositioned solution is re-*triaged*: this sweep read four solution bodies, four assumption nodes and several test nodes to re-derive conclusions that were already written on the nodes in full. The cost is per-pass and compounding, and it falls hardest on exactly the nodes prior passes thought hardest about.

**The concrete ask, which the three solutions beneath this node do not quite cover.** They address holds an operator places deliberately. This is narrower and cheaper: the outstanding-work computation should read the dispositions the tool's own writes already record — at minimum treat `status: shipped` as answering "why is there no instrument", since a red-now instrument for shipped behaviour is forbidden by the ruleset and the bucket is therefore asking for something no pass is permitted to supply.

_Observed by the 2026-08-05 unattended sweep across a pass boundary — the prior pass's remedy is on disk and dated, and the bucket's response to it is today's `ost_next_work` output. Grounds usability of the tool surface, not demand._
