---
type: Solution
status: unvalidated
source: 'agent:P3_ideate'
created: '2026-07-24'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A stall is definable well enough for a watchdog to act on it]]

A watchdog outside the agent tracks liveness, restarts stalled or crashed passes, and publishes a plain signal of whether the process is alive and when it last made progress — so "is it still running?" is answerable without inspecting anything.

**How it differs from its siblings:** addresses halting rather than corruption or drift, and is the only sibling that produces a continuously visible trust signal instead of a guarantee the operator has to take on faith.

**Trade-off:** a supervisor that restarts a subtly broken pass will loop forever, spending compute while looking healthy.

**Riskiest assumptions to test:** that "making progress" can be defined crisply enough to detect a stall (feasibility); that a liveness signal is what converts worry into walking away (desirability).

Status: agent-originated candidate. Unvalidated.

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 unlinked [[Replay historical runs against a stall definition]] — moved under [[A stall is definable well enough for a watchdog to act on it]] — the belief this test measures now has a node of its own

## Issues
- 2026-07-25 Cross-branch relation (twenty-passes P5, 2026-07-25): new solution 'Supervisor heartbeat consumes run journals and alerts on error' (under 'A failed pass reports success…') extends this node's contract rather than competing with it. If a human promotes either, build them as one thing.

## Definition of done

[[Replay historical runs against a stall definition]]

```
npx vitest run test/loop/stall-definition-replay.test.ts
```

Red today: no stall definition exists in the repository — nothing separates a pass making slow progress from one that has stopped. Green when a candidate definition replayed over every journal in `.ost-agent/runs/` flags every known stall and raises no false alarm on a healthy run.

**Read the green narrowly.** This command decides whether a stall is *detectable* from journals as they already exist. It does not decide that automatic restart is safe, and this solution proposes automatic restart. The node's own pre-committed reasoning is the reason to hold that line: one false restart of healthy work is worse than no supervisor at all, because it burns compute while looking alive. A detector with zero false alarms on the recorded sample is evidence, not a guarantee, and the sample is small.

So the honest sequencing is that a green here promotes the *reporting* sibling — tell a human the run looks stalled — and leaves restart needing its own argument about what happens when the detector is wrong.

**What this does not settle.** Desirability and viability are untouched: nothing here says an operator wants a supervisor, or would trust one enough to leave it running, which is the claim [[Trust an unmonitored agent enough to walk away]] actually turns on.
