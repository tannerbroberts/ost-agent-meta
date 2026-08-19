---
type: Opportunity
source: >-
  INBOX:2026-08-19-build-loop-stuck-ask-the-open-question-first-and-offer-options-only-once-the-.md
created: '2026-08-19'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion
[[Exclude any node with status deferred from build-loop target selection]]
[[Have the build loop re-read a target's current status immediately before committing to it, not a cached snapshot]]
[[Have the build loop keep its own do-not-reselect ledger for targets whose instrument stayed red after a build, independent of vault status]]

**The need (operator's voice, inferred from repeated automated build notes):** "I marked a solution `deferred` on 2026-08-16 because the data disproved it. The build loop kept picking it as a target anyway — on 2026-08-16 and again on 2026-08-19 — and spent a full firing re-deriving the exact same falsification each time. If `deferred` doesn't actually stop the loop from touching a node, I can't trust that any status I set holds while I'm not watching."

**Why it matters:** the whole value of an unattended loop is that it spends its cycles on what's actually outstanding. A target-selection step that ignores `status: deferred` burns real build-loop firings (each one a full plan/build/verify cycle) re-confirming a result the tree already recorded, while genuinely unbuilt solutions wait. It also erodes the one signal a human has for "stop working on this" — if deferring doesn't reliably exclude a node, the operator has no cheap way to make the loop leave something alone.

**Evidence:** the Solution node "Ask the open question first, and offer options only once the frame is agreed" was set `status: deferred` on 2026-08-16 with the falsifying data recorded in its History. The build loop nonetheless re-selected it as a build target and reported "not shipped" a second time (INBOX:2026-08-16-build-loop-stuck-...) and a third time three days later (INBOX:2026-08-19-build-loop-stuck-...), each report reproducing the identical falsification (two-stage framing costs 92 operator turns vs one-stage's 72 across 46 recorded questions). The build loop's own third report states explicitly: "the vault node was never updated after the first two runs to reflect that the assumption failed" — which is itself factually wrong (the node was updated on 2026-08-16), suggesting the loop's target-selection logic either does not check `status`, or is reading a stale copy of the node rather than the current one.

**Litmus test (more than one way to address?):** yes — filter build-loop target selection on `status != deferred`; have the loop re-read the node's current status immediately before committing to a target rather than caching an earlier snapshot; have the loop write a short-lived "do not re-select" marker when a target fails its own instrument, distinct from the tree's own deferred status; surface a loop-side alert when the same target is selected twice with an unchanged node file. Passes.

**Provenance:** rests on two automated build-loop notes (INBOX channel) plus the target Solution node's own History; not corroborated by a first-party recording (TRANSCRIPT) of the loop's selection logic itself, so held at the floor rung until one exists.
