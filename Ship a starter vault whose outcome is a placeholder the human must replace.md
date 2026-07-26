---
type: Solution
status: unvalidated
source: 'agent-run:autonomous-loop-2026-07-25-pass6'
created: '2026-07-25'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Does a placeholder outcome get replaced, or does it become the tree's real root]]

**The idea, including the part that is uncomfortable.** `npx ost-agent init` with no
arguments scaffolds a complete, working vault immediately — git, config, inbox, and a
root Outcome node whose body is an explicit placeholder that says, loudly and in the
node itself, that it is not yet the operator's mandate and that everything beneath it
is provisional until they run `set-outcome`. Setup then genuinely does run itself, and
the founder's sentence becomes literally true.

**Why it is worth holding as a candidate rather than dismissing.** The competing
solutions all pay for correctness with a question, and a question is exactly where a
curious stranger leaves. This one lets someone see a working artifact in fifteen
seconds and decide whether they care, which is the order most people evaluate tools
in. The append-only design also makes the fix cheap: `set-outcome` preserves the prior
mandate in the root's history, so replacing a placeholder is a normal, recorded act
rather than a repair.

**Why it may be wrong, and this is the whole argument against it.** The Outcome is the
one thing the agent is forbidden to invent, and a placeholder is an invention wearing
a disclaimer. Every node created before it is replaced ladders up to a goal nobody
chose, and the believability ladder has no rung for "mapped against a mandate that was
not real". Worse, placeholders are sticky: the thing most likely to happen is that a
stranger runs a pass against the placeholder, gets a plausible-looking tree, and never
replaces it — at which point the product has produced a confident artifact about
nothing, which is the failure this whole vault exists to prevent.

**How it compares.** It is the only sibling that can make *"setup runs itself"*
literally true, and the only one that trades away the rule the rest of the system is
built on. Those are the same sentence.

**Sequencing note.** Do not build this without running the assumption test beneath it.
It is the cheapest solution to build here and the most expensive to be wrong about.

⚠️ Unvalidated, and proposed against the agent's own design instincts — recorded
because a consideration set of one is not a consideration set.
