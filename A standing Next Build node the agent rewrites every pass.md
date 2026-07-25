---
type: Solution
status: unvalidated
source: 'agent-ideation — generalized from tetrix-ost commits bfa741b, 2328e61'
created: '2026-07-25'
---
#Solution #ported-from-ost-agent-vault
[[Does a briefing node change which node a builder actually opens first]]

**The idea.** One node, always at the same address, holding the agent's current reading of what to do next and why — rewritten (append-only, so the history is the record) at the end of every pass. Not buried in root annotations. Not a decision; a briefing.

**Why this is the cheapest thing that could work.** Both running instances already produce this content. They just produce it in the wrong place. The tetrix agent's final act was a 400-word annotation on the root Outcome titled *"What a builder should build next — surfaced, explicitly not decided"* — a genuinely excellent piece of prioritization reasoning, appended to the bottom of a node that already carried six other long annotations about unrelated concerns. The root Outcome has become an undifferentiated queue of things a human needs to decide, and the one thing a builder most needs to read is at the bottom of it.

Give that content its own address and it becomes findable. Nothing else in the tree changes.

**What good looks like — and the tetrix agent modelled it well enough to copy.** Its briefing had four parts: the highest-leverage build with the reasoning that makes it checkable; an explicit statement that the highest-*leverage* build is **not** the highest-*information* action (interviewing five real players was, and it said so); the small number of cheap human decisions that gate everything; and a warning about its own bias. That last part is the one worth mandating. Left to itself an agent will steer toward work it can do alone, and the briefing is where it should be made to declare that pull so the reader can discount it.

**Relationship to the ranking solution.** These are complements that survive each other's failure. Unblocking-leverage ranking is structural and auditable but says nothing when a tree's tests are independent. A written briefing carries judgement a graph cannot, but is only as good as the agent writing it. Shipping the briefing first is defensible on its own: it needs no schema change, no declarations on existing nodes, and it puts today's already-good output somewhere a builder will find it.

**Where this fails.** A briefing that says the same thing five passes running is noise, and the operator learns to skip it — the same fate the root annotations just suffered. It probably needs to say what *changed* since the last one, not just what is true.

⚠️ Unvalidated. Proposed by an agent, from an agent's behaviour.
