---
type: Solution
status: unvalidated
source: 'agent:P3_ideate'
created: '2026-07-24'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Replay historical runs against a stall definition]]

A watchdog outside the agent tracks liveness, restarts stalled or crashed passes, and publishes a plain signal of whether the process is alive and when it last made progress — so "is it still running?" is answerable without inspecting anything.

**How it differs from its siblings:** addresses halting rather than corruption or drift, and is the only sibling that produces a continuously visible trust signal instead of a guarantee the operator has to take on faith.

**Trade-off:** a supervisor that restarts a subtly broken pass will loop forever, spending compute while looking healthy.

**Riskiest assumptions to test:** that "making progress" can be defined crisply enough to detect a stall (feasibility); that a liveness signal is what converts worry into walking away (desirability).

Status: agent-originated candidate. Unvalidated.

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule

## Issues
- 2026-07-25 Cross-branch relation (twenty-passes P5, 2026-07-25): new solution 'Supervisor heartbeat consumes run journals and alerts on error' (under 'A failed pass reports success…') extends this node's contract rather than competing with it. If a human promotes either, build them as one thing.
