---
type: Assumption
source: 'agent-run:autonomous-loop-2026-08-06'
created: '2026-08-06'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion

Feasibility, and it is the load-bearing belief: reconciliation is worth building only if "repair or replace it" can be decided mechanically without ever replacing something that mattered.

**Stated so it can be false.** If the states a left-behind worktree turns up in cannot be separated into safe-to-reset and must-not-touch by inspection alone, then a reconciling setup is a setup that sometimes destroys a live run's uncommitted work — a silent, data-losing failure traded for a loud, harmless one. The current failure at least announces itself and costs one firing.

The states are enumerable and that is what makes this answerable rather than a matter of opinion: absent, valid worktree on the expected branch, valid worktree on a different branch, worktree with uncommitted changes, detached HEAD, interrupted rebase or merge, a plain directory that is not a worktree at all, and a stale registration whose directory git still lists but which is gone from disk. The observed failure hit at least the second-to-last of these — `/tmp/ost-main` existed and `git worktree add` refused it.

The quieter risk this does not cover: inspection can only see the filesystem. A run that is alive and mid-build leaves a worktree that looks exactly like one abandoned by a run that died at the same moment. Distinguishing those needs a liveness signal, which is the sibling candidate's whole premise and deliberately not this one's.
