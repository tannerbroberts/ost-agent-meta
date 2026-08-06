---
type: AssumptionTest
source: 'agent-run:autonomous-loop-2026-08-06'
created: '2026-08-06'
evidence: assertion
threshold: >-
  All 10 dismissals carry actor, timestamp and a non-empty reason; one command
  lists them; each is reversible to unmapped; and a dismissal with an empty or
  whitespace reason is refused — 5 of 5 properties.
instrument: npx vitest run test/ost/evidence-dismissal-audit-trail.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Who runs it.** An attended session with a build environment, or a human. This pass could not set a lane label — that is a human's `ost-agent lane --set`.

**What this measures.** Dismiss ten evidence records, then assert the mechanical half of auditability: each records who dismissed it, when, and why; one command lists them for review; each can be returned to `unmappedEvidence`; and a dismissal with an empty or whitespace-only reason is refused at the boundary rather than stored.

**The bar, pre-committed.** 5 of 5. The refusal is not optional decoration — an empty reason is how bulk dismissal actually looks in practice, and a mechanism that stores one has kept a log rather than a check. This vault has already seen the shape: an empty annotation being recorded rather than refused is on file as its own friction.

**Why it is red today.** There is no dismissal at all. The skill instructs the agent to skip an item that reveals no genuine need, and provides nothing to skip with, so the instruction and the tool surface disagree — this pass read four records in full, judged all four redundant, and had no way to record it. Every assertion in the spec fails against an absent action.

**What a green run does NOT settle — and this is the important half.** It settles that a dismissal is *recorded* honestly. It says nothing about whether recording restrains anybody. The parent assumption's real risk is that nobody reads the log: the operator this is built for has stated their hours do not exist, and an after-the-fact review queue is precisely the obligation such an operator never serves. Whether a reason string is a restraint or a formality the dismissing party writes to itself cannot be answered by building it, and a human should weigh that before this candidate is chosen over its siblings. A green run here is permission to trust the plumbing, not permission to grant the power.

## History
- 2026-08-06 body edited — The body declared "Lane: compute-only", which this pass had no power to set — `ost_flag_humans_required` is withheld on this surface and only a human's `ost-agent lane --set` moves what compute may run. The node carries no `lane:` field, so its effective lane is needs-humans (confirmed: it landed in `assumptionWork.needsHumans`), and the prose contradicted that. Replaced with the vault's established "Who runs it" phrasing.
