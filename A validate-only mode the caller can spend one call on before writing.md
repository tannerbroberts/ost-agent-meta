---
type: Solution
source: 'agent-ideation:2026-08-30-unattended-sweep'
created: '2026-08-30'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[A validate-only call can run every check the writing call runs while leaving nothing behind]]

**Variation dimension: who-does-the-work. Position taken: the agent carries it, by choosing to spend a cheap call it controls.**

Add a `validate: true` flag to the mutating tools. When set, the tool runs every check it would normally run — schema and semantic — writes nothing, and returns the complete list of objections. The caller decides when to spend it: on a call it is confident about, never; on a first `ost_create_node` for an AssumptionTest carrying both a `threshold` and an `instrument`, always.

**Why this position and not another.** The refusal path is left exactly as it is. Nothing about how a real call fails changes, no check is reordered, and no existing behaviour is at risk — the surface simply gains a way to ask "would this work?" without finding out the expensive way. That puts the work on the agent rather than on the surface's error handling, which is the honest reading of who actually has the information about whether a call is worth pre-checking.

**What it deliberately does not do.** It does not make the ordinary refusal any more informative. A caller who does not use the flag pays exactly what it pays today, three turns for three defects. This candidate buys an *option*, not a fix, and a surface where the good path is opt-in is a surface where the default path stays bad.

**What it gives up, plainly.** It adds a round trip to the common case if used reflexively — a caller that validates before every write has doubled its call count to avoid an occasional retry, which is worse on a queue of correct calls than doing nothing. It needs a discipline nobody can enforce, and the agent that most needs it is the one least likely to know it does. And it widens the tool surface: every mutating tool grows a parameter, and a `validate` flag that is silently ignored by one tool is a trap worse than the problem.

**Cheapest form.** One optional boolean on the mutating tools, checked in the dispatcher immediately before `tool.run(args)` is awaited — run the same validation, return the accumulated problems, skip the call. It needs the accumulation that the sibling candidate builds, so if that sibling is built this becomes nearly free; if it is not, this candidate has to build a second copy of the same collection logic, which is a reason to sequence it second.

**How it would be wrong.** If most multi-defect calls come from an agent that did not know a rule existed, a flag it also does not know about helps nobody. This is the right pick only if callers are aware of the grammars and get them wrong anyway — which nothing here has measured.

**Honest note on how this was ideated.** The sweep asks for one blind ideator per dimension. This surface holds no grant to run independent parallel ideators, so all three candidates under this opportunity were composed in one context by one author — the exact condition the blind-ideation rule exists to prevent. Read them as one author's three answers and discount their apparent distinctness accordingly.

Unvalidated. Agent-ideated 2026-08-30; a human to review.
