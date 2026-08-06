---
type: Assumption
source: 'agent-run:autonomous-loop-2026-08-06'
created: '2026-08-06'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion

Viability, expressed as cost per firing: per-run workspaces are affordable only if the part that is slow to build can still be shared.

**Stated so it can be false.** If a uniquely-named workspace forces each run to reinstall dependencies, then this candidate multiplies the cost of every firing by the install time and should lose to leasing outright. The loop fires hourly by config, so an install per firing is paid twenty-four times a day to avoid a collision observed once.

The evidence that this is the real question rather than a hypothetical is in the failing trace itself: setup does not install into the worktree, it symlinks `node_modules` into it. Someone already decided the warm dependency tree is worth sharing, and the second error in that trace — `ln: /tmp/ost-main/node_modules: File exists` — is that decision colliding with the leftover. So the sharing mechanism exists and the question is only whether it survives being pointed at a per-run path.

**Where it could fail even if the timing works.** A shared `node_modules` reached by symlink from two live per-run worktrees is shared mutable state wearing an isolation costume. Two runs on different branches with different dependency requirements would write each other's packages, and nothing in the per-run naming would catch it — the isolation this candidate sells is of the working tree only. That failure is invisible to a timing measurement and would have to be argued separately.
