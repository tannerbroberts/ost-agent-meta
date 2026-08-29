---
type: Solution
source: 'INBOX:2026-08-10-founder-theory-axioms-and-theory-space-proof.md'
created: '2026-08-10'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[Axiom asks arrive rarely enough to be answered instead of batched into ignorance]]

No register up front. When a derivation could move a node but rests on an axiom nobody has accepted, that axiom becomes one outstanding ask in the standing queue the operator already clears at their own cadence. Accept and the derivation proceeds and the axiom is recorded for reuse; reject and the derivation is filed as closed. The axiom set grows lazily, and every entry was accepted at a moment it visibly mattered.

**Contrast with siblings.** Against "A standing axiom register the human curates, which every derivation must cite": no up-front session to schedule and no shelf axioms — but every first-use derivation blocks on a human answer, so theory work is only as unattended as the queue is short. Against "Borrow the axiom set from a named body of practice and let the human only veto": each acceptance is a real felt-out judgement in context, at the cost of making them one at a time forever.

**Sharpest risk:** viability — whether asks arrive rarely enough to be answered rather than batched into ignorance.

## Issues
- 2026-08-29 2026-08-28 unattended sweep, repo sight held: examined for a missing instrument and deliberately left without one. Recording the examination because this node carried no prior note and would otherwise be re-read from scratch by every firing that meets it in `solutionsMissingInstruments` — which is the re-derivation cost its siblings already record. The belief beneath it, "Axiom asks arrive rarely enough to be answered instead of batched into ignorance", is a viability judgement about one person's answering behaviour over time: it needs a real queue to accumulate real asks and then the operator to say whether the arrival rate was tolerable. Neither half is a spec, and this node's own prose already names viability as its sharpest risk. Note also that the ask-queue machinery this candidate would ride on already exists and is populated — `ost_next_work` reported 52 outstanding asks this pass, all 52 predating ask tracking and carrying no recorded age — so the rate question could be answered from that ledger once the asks carry timestamps, which is a cheaper route than building anything here. What a human should do: set the lane with `ost-agent lane --set`, since `ost_flag_humans_required` is withheld on the unattended surface. Not a skipped step.
