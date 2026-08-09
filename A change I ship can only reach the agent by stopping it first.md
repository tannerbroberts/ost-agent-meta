---
type: Opportunity
status: unvalidated
source: >-
  tree-restructure:2026-08-05 — split from the bucket that held these solutions
  directly
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion
[[Versioned workflow with scheduled hot-swap and rollback]]
[[Canary the changed process against the old one]]
[[Agent proposes its own workflow changes for one-click adoption]]
[[Improvements I ship never reach the agents already running]]

**The need (customer's voice):** "Every time I want the agent to work a little differently, I have to stop it, change it, and start it over — and I lose the thread of what it was doing. So I put off improvements, and it keeps working the old way."

The running process holds its policy from when it started. Shipping an improvement means killing the run, and killing the run costs whatever it was in the middle of — so improvements queue up behind a restart nobody wants to spend, and the agent keeps running the version I already know is worse.

**Why it matters:** a system meant to run unattended has to be able to change *while* running: swap part of its own workflow, keep continuity, and back out if the change makes things worse. Otherwise unattended operation and improvement are mutually exclusive, and the operator becomes the bottleneck for both — putting off every improvement precisely because the system is doing something.

**Litmus test (more than one way to address it?):** several directions — scheduled update-and-restart windows, versioned workflow definitions with rollback, canarying a changed process against the old one, letting the agent propose workflow changes for one-click human adoption. Passes.

**Schema evolution is a form of this that the framing above does not name.** `INBOX:2026-07-24-friction-a-new-node-level-requirement-is-unfixable-for-ex.md`: adding the evidence-class invariant flagged all 57 then-existing nodes, and the append-only design had no generic edit path — every new required frontmatter field needs its own purpose-built `ost_set_*` tool before an existing tree can comply. The 2026-07-24 hard-fix pass hit this exact wall, and rungs had to be applied by human-authorized direct edit because `ost_set_evidence` was not in the shipped CLI. So the interruption is not only "restart the process": it is also "the improvement cannot reach work that already exists". Two independent instances, observed.

**Placement note for a human — carried over unresolved.** This plausibly nests under *"What the agent learns doesn't accumulate over time"* (self-improvement as compounding) as well as where it sits (continuity of unattended operation). Placed by the felt pain, which is interruption; flagged rather than double-linked, per the single-best-fit-parent rule. A human should confirm the parent.

Evidence: `INBOX:2026-07-24-opp-self-replacing-workflow.md`, and the friction record named above.

## History
- 2026-08-09 body edited — Repairing a defect this pass introduced in the merge of 2026-08-09, not a change of meaning. The `prose` passed to `ost_merge_nodes` began with its own `#Opportunity` tag line and a copy of the four child wikilinks, and the tool preserved the node's existing header block and appended that prose beneath it — so the tag line appeared twice and "Versioned workflow with scheduled hot-swap and rollback", "Canary the changed process against the old one", "Agent proposes its own workflow changes for one-click adoption" and "Improvements I ship never reach the agents already running" were each wikilinked twice from this one file. Four second backlinks, which is the single-backlink rule (`check` rule single-backlink) broken four times by the write that was supposed to reduce duplication. This edit restores exactly one header block and one edge per child; the prose below it is unchanged in substance. Recorded rather than quietly fixed because the cause generalises: `prose` on a merge is the body only, and a caller that hand-writes the link block gets a duplicate rather than a refusal.
