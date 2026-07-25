---
type: Opportunity
status: unvalidated
source: 'INBOX:2026-07-24-opp-idempotent-runtime.md'
created: '2026-07-24'
evidence: assertion
---
#Opportunity #unvalidated #needs-customer-interview #evidence/assertion
[[Improving how the agent works means interrupting it]]
[[Resumable append-only process journal]]
[[Supervisor heartbeat with automatic restart]]
[[Immutable goal contract]]
[[Two agents sharing my vault can trample each other]]
[[A failed pass reports success, so my automation can't tell]]

**The need (customer's voice):** "If I hand a goal and some compute to an autonomous agent and walk away, I need to come back to a system that is still running and still pointed at the same goal — and if I stop it or it crashes mid-step, I need to be able to start it again without wondering what got half-written."

**Why it matters:** The whole promise is that goal + compute drive discovery without supervision. Any doubt about halting, drift, partial writes, or stuck locks collapses that promise back into babysitting, which costs more attention than doing discovery by hand.

**Litmus test:** Several plausible directions — crash-safe append-only writes, resumable checkpoints, a supervisor that restarts work, a visible liveness signal, a goal-immutability guarantee. Passes.

**Provenance caveat:** Founder-stated and unvalidated. It is a trust need, so the real test is whether stakeholders actually walk away — observed behavior, not stated intent.

Evidence: `INBOX:2026-07-24-opp-idempotent-runtime.md`

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule

## Issues
- 2026-07-25 Near-synonym top-level sibling of 'Trust an unmonitored agent enough to walk away' — the children happen to partition (safety/honesty vs runtime continuity) but the titles do not carry the boundary; a reader cannot predict which child lives where. Merge-or-rename candidate for human decision (2026-07-24 review).
