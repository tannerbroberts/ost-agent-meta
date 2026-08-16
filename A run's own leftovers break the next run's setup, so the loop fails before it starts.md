---
type: Opportunity
source: 'TRANSCRIPT:0f940e60-26f9-459a-ace4-5af5ce438e2b'
created: '2026-08-06'
evidence: observed
---
#Opportunity #unvalidated #evidence/observed
[[Setup reconciles the workspace it finds instead of assuming there isn't one]]
[[Each run gets a workspace named after itself, so two runs cannot collide]]
[[The workspace is leased, and the next run reclaims a lease whose holder is gone]]

An unattended firing died before it did any work, and the thing that stopped it was the previous firing's residue.

**The need:** I want a run to start from a workspace in a known state, however the last run ended.

## What was observed

`TRANSCRIPT:0f940e60-26f9-459a-ace4-5af5ce438e2b` (2026-08-06T21:57Z, nobody watching) carries two tool errors and nothing else:

- `Preparing worktree (checking out 'main')` → `fatal: '/tmp/ost-main' already exists`, then `ln: /tmp/ost-main/node_modules: File exists`
- `fatal: not a git repository (or any of the parent directories): .git`

The shape is worth stating precisely, because it decides what would fix it. Setup is written as if the workspace is absent: it creates a worktree at a **fixed path** and symlinks `node_modules` into it. Both steps assert absence. A previous run that ended without tearing down leaves both present, so both fail — and the second error shows the cost compounding, because after the failed setup the session was left running git commands somewhere that is not a repository at all.

This is a failure at time zero. The run did not do part of its work badly; it never reached its work, and it burned a firing to find that out.

## Why this is not one of the needs already on the tree

- It is not the rediscovered-refusal census. Nothing here was refused by a guard and nothing was relearned; a command that would have worked against a clean machine met a dirty one.
- It is not repo sight. The path was reachable; it was occupied.
- It is not "I can't tell what a half-finished run actually finished". That need is about reading a dead run's record. This one is about the dead run's *debris*, which breaks the next run whether or not anyone can read what it finished.

## Litmus — more than one way to address it

Reconcile an existing workspace rather than assuming absence; give each run its own workspace so collision is impossible; or lease the shared one and let the next run reclaim an abandoned lease. Three different bets about whether the fix is idempotency, isolation, or lifecycle.

## Provenance

Observed behaviour of this product's own loop, captured mechanically from a session transcript with no narrator. It grounds reliability of the unattended loop, not demand: it is not evidence that anyone outside this building wants any of this.

## Corroborating instance — 2026-08-11 (named in plain text; discharges nothing)

`INBOX:2026-08-11-observed-build-loop-reports-not-merged-on-merged-prs.md` — a scratch worktree at `/private/tmp/ost-main-check`, created by the session that built the "check the tree you inherited builds" feature and never removed, stayed pinned at PR #93's merge commit. Every later `gh pr merge --delete-branch` then failed its local switch-to-main, so the build loop reported "NOT MERGED" on PRs #94 and #95 that GitHub shows merged — the leak was one session's, and the cost was paid by every firing after it, exactly this node's claim. The same leak stranded the shared checkout on a merged feature branch, so the discovery loop read its policy from a stale branch. Cleaned up by hand in an attended session (worktree removed, checkout returned to main, merged branches deleted); the source note proposes that a session which creates a worktree owns its removal, and that a preflight could refuse on a foreign worktree holding `main` — both are candidate directions beneath this node, not built and not validated.

## Corroborating instance — 2026-08-16 (named in plain text; discharges nothing)

`INBOX:2026-08-16-audit-loop-efficiency-and-checkout-drift.md` — an attended audit session observed that both the discovery loop and the build loop execute their automation scripts directly from whatever branch is checked out in the single shared working directory (no worktree isolation). A build session's own `git checkout -b <branch>` step leaves that branch checked out afterward; this repo sat on branch `two-stage-question-stop-count` for the length of that solution's whole stuck period, so every later firing of both loops ran automation code from that branch rather than from reviewed `main`, until the audit session manually reset it. In this instance the drift was harmless — the stuck branch never touched `examples/automation/*.sh` — but the build agent's grant includes unrestricted `Write` against the whole repository, including its own policy scripts (`examples/automation/build-pass.sh`), and nothing currently stops a future build session from editing that script, leaving its branch checked out, and having the edited script become the executable policy for every subsequent firing of both loops with no review in between. Evidence class for the risk itself: **inferred**, not observed — no session has done this yet; the observed part is the branch-drift mechanism, corroborating this node's existing 2026-08-11 instance where the same leak stranded the shared checkout on a stale branch and the discovery loop read its policy from it. Worth a human decision: whether the shared checkout should be reset to `main` at the START of each firing (before reading which script to run), independent of what the last firing left behind — a fourth candidate direction beneath this node, alongside reconcile/isolate/lease: reset-to-known-ref before each firing regardless of prior teardown.
