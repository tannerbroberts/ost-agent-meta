---
type: Opportunity
status: unvalidated
source: 'INBOX:2026-07-24-builder-loop-stopping-blocked-on-one-human-test.md'
created: '2026-08-02'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion
[[My unattended run stops at a prompt that assumes a person is sitting there]]
[[Announce the wait on a channel the operator already watches, the moment it starts]]
[[Bank the blocked item, carry on with everything independent of it, and present the block at the end]]
[[A standing queue of pending asks the operator clears at whatever cadence suits them]]

At the end of five building passes the tree held 24 solutions, none of them tested, every one of them blocked by the evidence gate. The binding constraint had stopped being engineering capacity: no agent may run an assumption test, so nothing in the loop could clear a single gate, and the loop's honest option was to stop building. One command from one person would have unblocked it — and nothing anywhere told that person it was waiting.

That is the shape of the problem, not the size of it. Compute can carry the work right up to the boundary where reality has to be touched, and then it stalls silently on the far side of a person's attention. The queue of things waiting on a human is invisible precisely to the human it is waiting on, so the cost shows up as passes that produce nothing rather than as a request anyone declined.

**The need:** when everything I have is blocked behind something only I can do, I want to be told which single action unblocks the most, without going looking for it.

More than one way to address this: surface the pending human actions as a ranked queue with the exact command, push the ask outward when a run ends blocked, age the outstanding asks so a stale one becomes visible, or let the loop stand down and say why rather than spend another pass discovering the same wall.

## Provenance

Distilled from `INBOX:2026-07-24-builder-loop-stopping-blocked-on-one-human-test.md` — the builder loop's fifth-pass report, which stopped rather than build a sixth solution and named `Hand-distil three past sessions` as the cheapest unblocking test.

**For human review:** the same report asks a policy question this node deliberately does not answer — whether the builder should be hard-blocked by the gate or allowed to proceed while saying it is blocked. Five passes suggest a soft gate gets ignored, including by the agent that wrote it.

## Issues
- 2026-08-02 Created against a prior disposition — flagged by the pass that created it, 2026-08-02. The Outcome's ledger records `builder-loop-stopping-blocked-on-one-human-test` as ACKNOWLEDGED, no node, on 2026-07-24, with the reasoning that it reports the existence of `ost-agent result` in the repo but not in the shipped CLI, and belongs on the product bug list rather than in the tree. This pass created a node from it because the item showed as unmapped in `ost_next_work`, which cannot see that ledger. The need stated here — that a queue of work blocked on one person is invisible to that person — may still be real and distinct from the release-state bug the ledger filed. A human should decide whether it earns a node or whether the 2026-07-24 disposition stands and this should be archived.
