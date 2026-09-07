---
type: Solution
source: 'agent-ideation:2026-09-07-unattended-sweep'
created: '2026-09-07'
evidence: assertion
killIf: >-
  No operator turns the outward ping on within eight weeks of it shipping —
  `remote.enabled` stays false on every install anyone runs, including the
  founder's.
killBy: '2026-11-07'
authorship: machine
---
#Solution #unvalidated #evidence/assertion

**Variation dimension: who-does-the-work. Position taken: an outside party, because every in-host option shares the host's own failure mode.**

Each firing sends one ping to a service that is not this machine. The service holds the expected cadence and raises an alert when a ping fails to arrive on time. Detection lives entirely off the host; this repository contributes a ping and a cadence declaration and nothing else.

**Why this position and not another.** This is the only one of the three candidates that survives the most likely cause of the observed gap. If the host was off from 09-04 to 09-06, then a watchdog process on that host was off too, a heartbeat file on its disk stopped being written with nobody to read it, and the report that would have shown a liveness line was never generated because nothing ran to generate it. Absence of evidence is only detectable by something that expected evidence and is still running. That thing cannot be inside the box.

**What it deliberately does not do.** It takes no view on *why* the loop stopped and does no diagnosis. It answers one question — did a firing happen when one was due — and leaves the cause to whoever looks.

**What it gives up, plainly, and it is the sharp cost.** It requires network egress from a product whose config ships `remote.enabled: false` and whose tree carries a whole opportunity about not wanting systems of record connected outward. It introduces a third-party dependency, a second thing that can be down, and a channel that leaks at minimum the fact and timing of every firing. An operator who chose this product partly for being local-only is being asked to give that up to learn a single bit. That is a real trade and it may simply be refused.

**What would make this the wrong pick.** If operators will not enable outward anything, the alerting never turns on and this is dead code — which is exactly what the kill criterion checks.

**Honest note on how this was ideated.** The sweep asks for one blind ideator per dimension. This surface holds no grant to run independent parallel ideators, so all three candidates under this opportunity were composed in one context by one author — the condition the blind-ideation rule exists to prevent. Read them as one author's three answers and discount their apparent distinctness accordingly.

Unvalidated. Agent-ideated 2026-09-07; a human to review.
