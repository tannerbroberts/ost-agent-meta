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
[[Operators will open an outward channel from a local-only product just to learn it stopped]]

**Variation dimension: who-does-the-work. Position taken: an outside party, because every in-host option shares the host's own failure mode.**

Each firing sends one ping to a service that is not this machine. The service holds the expected cadence and raises an alert when a ping fails to arrive on time. Detection lives entirely off the host; this repository contributes a ping and a cadence declaration and nothing else.

**Why this position and not another.** This is the only one of the three candidates that survives the most likely cause of the observed gap. If the host was off from 09-04 to 09-06, then a watchdog process on that host was off too, a heartbeat file on its disk stopped being written with nobody to read it, and the report that would have shown a liveness line was never generated because nothing ran to generate it. Absence of evidence is only detectable by something that expected evidence and is still running. That thing cannot be inside the box.

**What it deliberately does not do.** It takes no view on *why* the loop stopped and does no diagnosis. It answers one question — did a firing happen when one was due — and leaves the cause to whoever looks.

**What it gives up, plainly, and it is the sharp cost.** It requires network egress from a product whose config ships `remote.enabled: false` and whose tree carries a whole opportunity about not wanting systems of record connected outward. It introduces a third-party dependency, a second thing that can be down, and a channel that leaks at minimum the fact and timing of every firing. An operator who chose this product partly for being local-only is being asked to give that up to learn a single bit. That is a real trade and it may simply be refused.

**What would make this the wrong pick.** If operators will not enable outward anything, the alerting never turns on and this is dead code — which is exactly what the kill criterion checks.

**Honest note on how this was ideated.** The sweep asks for one blind ideator per dimension. This surface holds no grant to run independent parallel ideators, so all three candidates under this opportunity were composed in one context by one author — the condition the blind-ideation rule exists to prevent. Read them as one author's three answers and discount their apparent distinctness accordingly.

Unvalidated. Agent-ideated 2026-09-07; a human to review.

## Issues
- 2026-09-07 2026-09-07 unattended sweep, repo sight held: examined for a missing instrument and deliberately left without one. Recording the examination because this node was ideated earlier today and carried no prior note. The belief beneath it — "Operators will open an outward channel from a local-only product just to learn it stopped" — is desirability about people outside this building, and no exit code can measure whether anyone would accept the trade this candidate names in its own body (network egress from a product that ships `remote.enabled: false`). The tree already carries the matching ask on its standing queue: "Ask five operators whether they would emit firing times off-host to be told the loop stopped". So this is the humans-required kind, not an un-done command, and an instrument written here could only measure that a ping was emitted — a fact about our code that says nothing about the belief. What a human should do: set the lane with `ost-agent lane --set`, since `ost_flag_humans_required` is withheld on the unattended surface. Nothing else changed — no instrument set, no status changed, no rung moved.
