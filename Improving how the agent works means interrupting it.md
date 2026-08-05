---
type: Opportunity
status: unvalidated
source: 'INBOX:2026-07-24-opp-self-replacing-workflow.md'
created: '2026-07-24'
evidence: assertion
---
#Opportunity #unvalidated #needs-customer-interview #placement-ambiguous #evidence/assertion
[[Improvements I ship never reach the agents already running]]
[[A change I ship can only reach the agent by stopping it first]]

**The need (customer's voice):** "Every time I want the agent to work a little differently, I have to stop it, change it, and start it over — and I lose the thread of what it was doing. So I put off improvements, and it keeps working the old way."

**Why it matters:** A system meant to run unattended has to be able to change *while* running: swap part of its own workflow, keep continuity, and back out if the change makes things worse. Otherwise unattended operation and improvement are mutually exclusive, and the operator becomes the bottleneck for both.

**Litmus test:** Several directions — scheduled update-and-restart windows, versioned workflow definitions with rollback, canarying a changed process against the old one, letting the agent propose workflow changes for one-click human adoption. Passes.

**Placement note for a human:** This plausibly nests under *"What the agent learns doesn't accumulate over time"* (self-improvement as compounding) as well as here (continuity of unattended operation). Placed here because the felt pain is interruption; flagged rather than double-linked. A human should confirm the parent.

Evidence: `INBOX:2026-07-24-opp-self-replacing-workflow.md`

## Issues
- 2026-07-24 Ambiguous parent (agent-flagged, 2026-07-24 pass). This opportunity fits two plausible parents: "I can't leave the process running unattended without worrying" (chosen — the felt pain is interruption of an unattended system) and "What the agent learns doesn't accumulate over time" (self-improvement as a form of compounding). Placed under the former and flagged rather than double-linked or duplicated, per the single-best-fit-parent rule. A human should confirm or re-parent.

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 unlinked "Versioned workflow with scheduled hot-swap and rollback" — re-parented under "A change I ship can only reach the agent by stopping it first" — this solution answers that need, not the categories beside it
- 2026-08-05 unlinked "Canary the changed process against the old one" — re-parented under "A change I ship can only reach the agent by stopping it first" — this solution answers that need, not the categories beside it
- 2026-08-05 unlinked "Agent proposes its own workflow changes for one-click adoption" — re-parented under "A change I ship can only reach the agent by stopping it first" — this solution answers that need, not the categories beside it

## Supporting evidence — observed friction (2026-07-24)

`INBOX:2026-07-24-friction-a-new-node-level-requirement-is-unfixable-for-ex.md`: adding the evidence-class invariant flagged all 57 then-existing nodes, and the append-only design had no generic edit path — every new required frontmatter field needs its own purpose-built `ost_set_*` tool before an existing tree can comply. Schema evolution is an interruption this opportunity did not yet name: the 2026-07-24 hard-fix pass hit this exact wall (rungs had to be applied by human-authorized direct edit because `ost_set_evidence` is not in the shipped CLI). Evidence class: observed behavior, two independent instances.
