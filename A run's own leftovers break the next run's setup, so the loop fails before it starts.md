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
