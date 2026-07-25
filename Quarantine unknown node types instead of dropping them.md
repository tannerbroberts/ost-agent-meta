---
type: Solution
status: unvalidated
source: 'agent-ideation — from ost_read_tree omitting the type:Metric node, 2026-07-24'
created: '2026-07-25'
---
#Solution #ported-from-ost-agent-vault
[[Does a quarantined node make the agent notice the hole in its tree]]

**The idea.** A node whose `type:` the reader does not recognize should come back from `ost_read_tree` marked unrecognized — not be omitted. Silence is the bug; the unknown type is just the trigger.

**The concrete failure.** `type:` was changed from `Opportunity` to `Metric` on one node in this vault. `ost_read_tree` now returns 49 nodes and that node is not one of them, so its 8 outgoing links are invisible too. Downstream, `ost_next_work` reports the consequences without the cause: 4 orphan Opportunities, 3 orphan Solutions, 1 dangling link — nine hygiene issues, none of which says *a node is missing*. An agent reading only the tools cannot recover the fact that a large branch exists on disk. It would confidently run a full pass against a tree with a hole in it and report success.

**This is a one-line-of-reasoning bug with an outsized blast radius**, and it is the most mechanically certain item anywhere in this tree — it is not a hypothesis about operators, it is reproducible in this working directory right now. Everything else here is proposed on the strength of one incident or one agent's behaviour; this one is just wrong.

**What "quarantined" should mean.** The node is returned, with its title, body, and links, flagged `unrecognized-type: Metric`. It does not participate in hierarchy validation, so it generates no bogus hygiene noise of its own. Its children are reported as *quarantined-parent* rather than *orphan*, which is the difference between a diagnosis and a symptom. And the unknown type value itself is surfaced to the human, because — as the sibling solution argues — an operator reaching for a type the schema lacks is a product signal worth reading, not an error to be normalized away.

**Scope discipline.** This is not the Context-node-type solution and should not be conflated with it. That one asks what types should exist; this one only insists that a node the agent cannot classify must still be *seen*. Build this even if the schema never changes — unknown types will also arrive from version skew, from a future release's node kinds, and from typos.

⚠️ Unvalidated as a customer need, though the defect itself is confirmed by direct observation.
