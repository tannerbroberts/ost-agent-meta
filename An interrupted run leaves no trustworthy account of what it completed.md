---
type: Opportunity
status: unvalidated
source: >-
  tree-restructure:2026-08-05 — split from the bucket that held these solutions
  directly
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion
[[Every recorded step carries the directory and argv it actually ran with]]
[[A run journal written as it goes, so an interrupted run reads as a list of finished steps]]
[[Reconstruct what finished from the commit history, so no run has to be trusted to report]]
[[A recorded failure can't be reproduced, because the record omits where it ran]]

The run's own report is written at the end, so a run that does not reach the end reports nothing. What it did finish has to be inferred from side effects, and the inference is unreliable precisely when it matters most — after a failure.

The sharper statement of the need is not that the account is missing but that it **cannot be trusted**. A record is often present; it is silent about the one variable that would let a reader use it. The operator's problem is not an empty log, it is a log that reads as authoritative and is not.

Litmus — more than one way to address this: progress markers and checkpoints, a run journal written as work happens, idempotent work detection, resumable pass state, or reconstruction from side effects nobody had to remember to write. Distinct from "What the agent learns doesn't accumulate over time", which is cross-session knowledge; this is intra-run work state.

## Grounding

A builder pass was backgrounded mid-work on 2026-07-24 and the next pass had no way to tell what it had finished from what it had abandoned (agent-filed friction, kind: `blocked`). That is the originating observation, self-reported by the agent rather than by an outside operator.

## The failure reproduced, with the missing variable named

Observed twice in one pass on 2026-07-27, and the gap is narrower and more fixable than the general framing suggests.

`ost-agent loop step` records the phase, the command string, the exit code and the duration. It does **not** record the working directory the command ran in. Twice that pass, `loop step ... -- npx vitest run` was invoked from the home directory instead of the repo; vitest collected all four sibling repos, exited 1, and the health record now carries a build step at exit 1 against a command that passes cleanly in its intended cwd. Both entries were left standing rather than edited — the exit codes are true, and laundering them is the one thing the seal discipline forbids.

The point is not the operator error. It is that the record is **honest about the exit code and silent about the single variable that explains it**, so the failure cannot be reproduced or diagnosed from the record alone. A reader six passes later sees `bash -c npx vitest run -> exit 1` and cannot distinguish a real regression from a mis-invocation.

Filed as `INBOX:2026-07-27-friction-loop-step-records-the-command-and-its-exit-code-.md`, kind `missing-affordance`, 2026-07-27T00:55Z, and mapped 2026-08-02.

This is direct confirmation of the candidate already sitting beneath this node, "Every recorded step carries the directory and argv it actually ran with" — the failure occurred, the record was kept, and the record could not be used to reproduce or attribute it. It does not validate that solution: no test has been run, and cwd is one of several variables that could have been the missing one. It moves the solution from inferred-need to observed-need, and it is the concrete case any assumption test beneath it should have to reproduce.

## History

Carried across from the node folded in here on 2026-08-07, reinstated verbatim rather than re-performed, so the record of the 2026-08-05 re-parenting is not lost with the file:

- 2026-08-05 unlinked "Every recorded step carries the directory and argv it actually ran with" — re-parented under "An interrupted run leaves no trustworthy account of what it completed" — this solution answers that need, not the categories beside it
- 2026-08-05 unlinked "A run journal written as it goes, so an interrupted run reads as a list of finished steps" — re-parented under "An interrupted run leaves no trustworthy account of what it completed" — this solution answers that need, not the categories beside it
- 2026-08-05 unlinked "Reconstruct what finished from the commit history, so no run has to be trusted to report" — re-parented under "An interrupted run leaves no trustworthy account of what it completed" — this solution answers that need, not the categories beside it
- 2026-08-07 merged "I can't tell what a half-finished run actually finished" into this node and deleted its file — Both state one need: after a run stops partway, the operator has no dependable account of which steps completed. The 2026-08-07 pass annotated them as near-duplicates and recommended exactly this direction and this survivor, but could not execute it — `ost_merge_nodes` requires the survivor's complete merged body and that pass had no way to read a node's body, so the prose could only have been written by discarding wording it had never seen. This pass read both files in full before composing the body below, so that blocker no longer applies. The survivor keeps the sharper framing (the account exists and cannot be trusted, rather than being absent) and the three solutions re-parented onto it on 2026-08-05; the loser's observed grounding, its cwd finding, and its History are folded in rather than dropped. The loser's edge to this node was detached first, so no self-link is unioned in.

## Issues
- 2026-08-07 2026-08-07 A merge returned an evidence item to the unmapped queue — observed immediately after this node absorbed "I can't tell what a half-finished run actually finished", and it is a mechanism finding rather than a fault in this node.

The folded node carried `source: INBOX:2026-07-24-friction-a-backgrounded-session-leaves-no-marker-of-where.md` in its frontmatter. That was the only node in the tree citing that item, and it is what discharged it from `ost_next_work`. Deleting the file deleted the citation. On the very next sweep the item reappeared in `unmappedEvidence` — the total went 77 → 78 across a pass whose ingest captured nothing new.

`ost_merge_nodes` carries the loser's prose, its edges and its reserved sections across, but not its `source`. This survivor's frontmatter still reads `tree-restructure:2026-08-05`, so the provenance now exists only in the body text above, which no sweep reads. Nothing was lost from the record; what was lost is the mapping.

Two consequences worth separating. The small one is local: this node's grounding is now weaker in frontmatter than it is in fact, and no tool on this surface can set `source`, so it cannot be repaired from here. The larger one is general — every merge of a node that mapped an evidence item silently re-opens that item, so a pass that pays down duplicate debt increases the unmapped backlog as a side effect. This pass performed two merges and produced exactly one such regression, because the other folded node's source was a TRANSCRIPT id also cited elsewhere.

For a human: the honest repair is for the merge to union the loser's `source` into the survivor's, the same way it unions edges. Until then, a merge should be treated as costing one re-opened evidence item whenever the loser was the sole citer. This bears directly on "Evidence that only confirms a need I already recorded still arrives as work I have to clear", where three candidate solutions were added this pass — none of them covers this case, and the corroboration candidate is the one that would.
