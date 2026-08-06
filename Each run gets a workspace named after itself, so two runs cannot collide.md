---
type: Solution
source: 'agent-run:autonomous-loop-2026-08-06'
created: '2026-08-06'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[The expensive half of a workspace can be shared while the mutable half is per-run]]

**The idea.** Delete the fixed path. Each run derives its workspace from its own run id — `/tmp/ost-<runid>` — so the question "is it already there?" cannot arise, because no other run has ever used that name. Teardown becomes best-effort rather than load-bearing: a leaked directory costs disk, not the next firing.

**Approach:** *isolation*. Remove the shared resource rather than arbitrate access to it.

**Contrast with its siblings.** The only one of the three that is correct even when two runs overlap. Reconciliation assumes serial runs and destroys a live one if that assumption breaks; leasing detects overlap but has to define liveness. This one is indifferent to how many runs exist, which matters because the tree already carries a separate need about two agents sharing one vault.

**Where it fails.** It gives up the warm workspace. The observed trace symlinks `node_modules` into the worktree, which is a cost-avoidance measure — a fresh path per run means either re-linking from a shared cache (fine, and probably what this becomes) or reinstalling per run (not fine, and would make every firing dramatically more expensive). So this candidate is only affordable if the expensive part of the workspace can be shared while the mutable part is not, and that split is unexamined. It also converts a loud failure into a quiet leak: nothing will tell the operator that `/tmp` is filling with dead workspaces until something else breaks.

**Cost.** A path derivation and a reaper for old directories. No decision table, which is its main advantage over reconciliation.

⚠️ Unvalidated. Agent-ideated from one observed failure.

## Definition of done

"Set up a per-run workspace and count what it reinstalls against the warm shared one"

```
npx vitest run test/runner/per-run-workspace-cost.test.ts
```

Green means a run-id-derived workspace reinstalls nothing and prepares within 20% of the warm shared path — the cost objection answered. It settles nothing about correctness: two live per-run worktrees sharing one dependency tree by symlink are isolated only in their working trees, and that failure stays green on every number this command reports.
