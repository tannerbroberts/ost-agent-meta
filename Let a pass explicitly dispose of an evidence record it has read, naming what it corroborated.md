---
type: Solution
source: 'agent-ideation:2026-08-22-unattended-sweep'
created: '2026-08-22'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

**Variation dimension: when it acts — this candidate drains at the moment of judgement, where both siblings drain by inspecting the tree afterwards.** A pass that has read an evidence record records a disposition for it on a ledger: `corroborates <node>`, or `reveals no need`, with a sentence of reasoning. The queue reads the ledger and stops offering what has been disposed of.

**Why this shape.** It is the only candidate that can drain a record which produced **no tree change at all** — and on this evidence stream that is most of them. The skill instructs a pass to skip an item revealing no genuine need, and skipping is currently indistinguishable from never having looked: the record returns next sweep and the sweep after, and every pass pays to re-read it and re-reach the same conclusion. Both siblings are blind to that case by construction, because both infer mapping from what the tree ended up saying, and a correct skip says nothing. This one also captures the reasoning, so the next pass inherits a judgement instead of repeating the work.

**Compared to its siblings.** The other two make a *correct corroboration* visible; this makes a *completed reading* visible, which is the larger set. It is also the only one that leaves an audit trail a human can review — 363 dispositions with reasons is a readable artifact in a way 363 silent drains is not.

**What would make this the wrong pick, and it is the sharpest objection in this set.** It hands the agent a button that makes its own inbox smaller. Every other mechanism on this surface that removes work from view is deliberately held away from the agent — retraction is a human's CLI act, `validated` is not a settable status, promotion is human-only — for the single reason stated throughout this codebase: a constrained actor must never be able to empty a gate's denominator on its own authority. A dismissal ledger is exactly that power, pointed at evidence. Mitigations exist (require a named node; make dispositions append-only and reviewable; let the queue keep a "disposed, unreviewed" count so nothing vanishes) but they are mitigations, and whether the trade is acceptable is the operator's call rather than this pass's.

⚠️ Unvalidated. Agent-ideated from this pass's own tool output.
