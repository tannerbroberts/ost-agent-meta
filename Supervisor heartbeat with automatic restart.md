---
type: Solution
status: unvalidated
source: 'agent:P3_ideate'
created: '2026-07-24'
---
#Solution #unvalidated

A watchdog outside the agent tracks liveness, restarts stalled or crashed passes, and publishes a plain signal of whether the process is alive and when it last made progress — so "is it still running?" is answerable without inspecting anything.

**How it differs from its siblings:** addresses halting rather than corruption or drift, and is the only sibling that produces a continuously visible trust signal instead of a guarantee the operator has to take on faith.

**Trade-off:** a supervisor that restarts a subtly broken pass will loop forever, spending compute while looking healthy.

**Riskiest assumptions to test:** that "making progress" can be defined crisply enough to detect a stall (feasibility); that a liveness signal is what converts worry into walking away (desirability).

Status: agent-originated candidate. Unvalidated.
