---
type: Solution
status: unvalidated
source: 'agent:P3_ideate'
created: '2026-07-24'
---
#Solution #unvalidated

The outcome is a locked contract: no autonomous process can alter it, any proposed change is raised as a visible question for a human, and every pass records which goal it ran against so drift is auditable after the fact.

**How it differs from its siblings:** addresses the second half of the trust worry — not "will it stop?" but "will it still be pointed where I left it?". Availability and crash-safety do nothing for this.

**Trade-off:** a locked goal that turns out to be mis-formed keeps compounding effort in the wrong direction; the escape hatch has to be easy for a human and impossible for the agent.

**Riskiest assumptions to test:** that goal drift is a real fear rather than a hypothetical one (desirability); that agents reliably raise rather than reinterpret an ill-fitting goal (feasibility).

Status: agent-originated candidate. Unvalidated.
