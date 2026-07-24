---
type: Opportunity
status: unvalidated
source: 'INBOX:2026-07-24-opp-self-replacing-workflow.md'
created: '2026-07-24'
---
#Opportunity #unvalidated #needs-customer-interview #placement-ambiguous
[[Versioned workflow with scheduled hot-swap and rollback]]
[[Canary the changed process against the old one]]

**The need (customer's voice):** "Every time I want the agent to work a little differently, I have to stop it, change it, and start it over — and I lose the thread of what it was doing. So I put off improvements, and it keeps working the old way."

**Why it matters:** A system meant to run unattended has to be able to change *while* running: swap part of its own workflow, keep continuity, and back out if the change makes things worse. Otherwise unattended operation and improvement are mutually exclusive, and the operator becomes the bottleneck for both.

**Litmus test:** Several directions — scheduled update-and-restart windows, versioned workflow definitions with rollback, canarying a changed process against the old one, letting the agent propose workflow changes for one-click human adoption. Passes.

**Placement note for a human:** This plausibly nests under *"What the agent learns doesn't accumulate over time"* (self-improvement as compounding) as well as here (continuity of unattended operation). Placed here because the felt pain is interruption; flagged rather than double-linked. A human should confirm the parent.

Evidence: `INBOX:2026-07-24-opp-self-replacing-workflow.md`
