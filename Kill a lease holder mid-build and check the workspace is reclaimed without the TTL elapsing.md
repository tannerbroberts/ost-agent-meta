---
type: AssumptionTest
source: 'agent-run:autonomous-loop-2026-08-06'
created: '2026-08-06'
evidence: assertion
threshold: >-
  A holder killed with SIGKILL is detected dead and its workspace reclaimed in
  under one firing interval, well short of the TTL; and across 20 trials against
  a live but slow holder, the workspace is reclaimed zero times. One false
  reclaim of a live holder refutes the assumption outright.
instrument: npx vitest run test/runner/workspace-lease-liveness.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**What this measures.** Two halves, and the assumption needs both. Take a lease, SIGKILL the holder, and assert the next run reclaims the workspace promptly rather than waiting for expiry — that is the half that distinguishes leasing from a plain timeout. Then hold a lease with a process that is alive but deliberately slow, run the reclaim path twenty times, and assert it never takes the workspace.

**The bar, pre-committed.** Stated in the threshold above. The asymmetry is deliberate: a missed death costs one delayed firing, while a false reclaim destroys a healthy run's work, so the second bar admits no failures at all where the first is merely bounded.

**Why it should be red today.** No lease exists at the workspace level. Setup takes the fixed path unconditionally, which is why the observed run collided with it rather than backing off or reclaiming. The only lease in the product is the loop-level one, and the config comment states its semantics plainly — `lockTtlMinutes: 60`, "a firing still holding the lock after this is assumed dead". A spec asserting detection rather than assumption fails against that mechanism on its meaning, not merely on a missing file.

**Honesty about that claim.** The `lockTtlMinutes` reading comes from this vault's own `ost.config.yaml`, which this pass did read. The claim that no workspace-level lease exists comes from the transcript, not from the code: product-directory reads were denied here and `ost_read_repo` was not granted. That second half is the weaker of the two and a builder should confirm it before trusting this node's framing.

**What a green run does NOT settle.** It shows liveness is detectable in the two cases staged — a killed process and a slow one. It says nothing about the cases that are genuinely hard and are why TTLs exist: a holder on a machine that slept, a holder whose process id was recycled, or a holder killed so abruptly that its heartbeat is fresh and its work is not. It also does not settle what a reclaiming run should do with whatever the dead one left in the tree, which is a separate design question this test deliberately does not reach into. And nothing here argues that leasing is worth its cost against the two cheaper siblings; that comparison is a human's.

## Instrument Log
- 2026-08-06 **red** (exit 1) `npx vitest run test/runner/workspace-lease-liveness.test.ts` — No test files found, exiting with code 1
