---
type: Opportunity
status: unvalidated
source: 'INBOX:2026-07-24-friction-a-backgrounded-session-leaves-no-marker-of-where.md'
created: '2026-07-25'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion
[[A recorded failure can't be reproduced, because the record omits where it ran]]
[[An interrupted run leaves no trustworthy account of what it completed]]

When a run is stopped, backgrounded, or dies mid-work, nothing marks where it got to. The next run — or the operator — cannot tell finished work from abandoned work, so it either redoes, skips, or guesses.

Grounding: a builder pass was backgrounded mid-work on 2026-07-24 and the next pass had no way to tell what it had finished versus abandoned (agent-filed friction, kind: blocked).

Litmus: progress markers/checkpoints, a run journal, idempotent work detection, resumable pass state — multiple distinct ways to address. Distilled by the mapping agent from agent-self-reported observation; unvalidated. Distinct from "What the agent learns doesn't accumulate over time" (cross-session knowledge) — this is intra-run work-state.

## Issues
- 2026-07-27 OBSERVED TWICE IN ONE PASS, 2026-07-27 (eleventh pass) — and the gap is narrower and more fixable than this node's general framing.

`ost-agent loop step` records the phase, the command string, the exit code and the duration. It does NOT record the working directory the command ran in. Twice this pass I invoked `loop step ... -- npx vitest run` from the home directory instead of the repo; vitest collected all four sibling repos, exited 1, and the health record now carries a build step at exit 1 against a command that passes cleanly in its intended cwd. Both entries are left standing rather than edited — the exit codes are true, and laundering them is the one thing the seal discipline forbids.

The point is not the operator error. It is that the record is HONEST about the exit code and SILENT about the single variable that explains it, so the failure cannot be reproduced or diagnosed from the record alone. A reader six passes from now sees `bash -c npx vitest run -> exit 1` and has no way to distinguish a real regression from a mis-invocation.

Cheapest fix: `loop step` stores `cwd` (and arguably the resolved argv) alongside the exit code. It is one field, and it converts an unreproducible number into a reproducible one. Filed as friction this pass; see "Resumable append-only process journal" for the adjacent structure this would extend.
- 2026-08-07 Near-duplicate of "An interrupted run leaves no trustworthy account of what it completed" — proposed merge, not executed. Both state the same need: after a run stops partway, the operator has no dependable account of which steps completed. That node already carries three solutions ("Every recorded step carries the directory and argv it actually ran with", "A run journal written as it goes, so an interrupted run reads as a list of finished steps", "Reconstruct what finished from the commit history, so no run has to be trusted to report"); this node carries none, which is why it is reported under-served on every pass. Recommended: merge this INTO "An interrupted run leaves no trustworthy account of what it completed", which keeps the subtree and the sharper framing (the account exists but cannot be trusted, rather than being absent). Not executed here because `ost_merge_nodes` requires the survivor's full merged body and no tool on this surface returns a node's body — see "The repair I am asked to make requires rewriting prose no tool will show me".

## Evidence — the failure reproduced, with the missing variable named (mapped 2026-08-02)

`INBOX:2026-07-27-friction-loop-step-records-the-command-and-its-exit-code-.md` — kind `missing-affordance`, filed 2026-07-27T00:55Z by the loop.

`loop step --phase build -- npx vitest run` was run from the home directory instead of the repo. vitest collected all four repos and exited 1. The health record now holds an exit-1 against a command that passes in its intended cwd, and the filing's own summary is the sharpest statement of this opportunity yet written: **"The record is honest about the exit code and silent about the one variable that explains it."**

This is direct confirmation of the candidate already sitting under this node, "Every recorded step carries the directory and argv it actually ran with" — the failure occurred, the record was kept, and the record could not be used to reproduce or attribute it. It does not validate that solution (no test has been run, and cwd is one of several variables that could have been the missing one), but it moves the solution from inferred-need to observed-need and is the concrete case any assumption test under it should have to reproduce.

## History
- 2026-08-05 unlinked "Every recorded step carries the directory and argv it actually ran with" — re-parented under "An interrupted run leaves no trustworthy account of what it completed" — this solution answers that need, not the categories beside it
- 2026-08-05 unlinked "A run journal written as it goes, so an interrupted run reads as a list of finished steps" — re-parented under "An interrupted run leaves no trustworthy account of what it completed" — this solution answers that need, not the categories beside it
- 2026-08-05 unlinked "Reconstruct what finished from the commit history, so no run has to be trusted to report" — re-parented under "An interrupted run leaves no trustworthy account of what it completed" — this solution answers that need, not the categories beside it
