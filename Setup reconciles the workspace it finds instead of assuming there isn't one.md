---
type: Solution
source: 'agent-run:autonomous-loop-2026-08-06'
created: '2026-08-06'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

**The idea.** Make setup converge on the state it wants rather than assert the state it expects. Before creating the worktree, look: if the path is absent, create it; if it holds a valid worktree on the right branch, reuse it; if it holds something else, repair or replace it. Same for the `node_modules` symlink — a link already pointing at the right place is success, not `File exists`.

**Approach:** *idempotency*. The operation's second run is a no-op instead of an error.

**Contrast with its siblings.** This is the only one of the three that keeps a single warm workspace, which is what makes a firing cheap — the symlinked `node_modules` in the observed trace exists precisely so every run does not reinstall. Per-run isolation throws that away; leasing keeps it but needs a liveness notion this does not. It is also the smallest change: no new state, no new file, no coordination between runs.

**Where it fails, stated so it can be judged.** "Repair or replace it" is the whole difficulty hiding in a clause. A worktree can be dirty in ways that are not mechanically distinguishable from work in progress — uncommitted changes, a detached HEAD, a half-applied rebase — and a setup that cheerfully replaces those is a setup that can destroy a run that was still going. That is the failure this candidate trades for the one it fixes, and it is worse, because it is silent. It is only safe if no second run is ever live at the same time, which this candidate assumes and does not enforce.

**Cost.** A stat-and-branch in the setup path, plus a decision table for the states a worktree can be found in.

⚠️ Unvalidated. Agent-ideated from one observed failure.
