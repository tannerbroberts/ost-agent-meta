---
type: Assumption
source: 'agent-ideation:2026-08-09-unattended-sweep'
created: '2026-08-10'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Compute a route over a tree that encodes no ordering and require a refusal]]

**The belief, stated so it can be false.** The edges the tree already holds are sufficient to compute a route — an ordered chain from where the reader is to the goal state — without any new declaration on any existing node.

This is the feasibility half of this solution, and it is separate from the desirability half already recorded beneath it. The solution's other assumption, "Seeing a path instead of a taxonomy changes which work a builder starts on", is a claim about what a person does differently and no exit code observes one. This one is a claim about whether the data supports the render at all, and it is settled by code.

**Why it could be false, in the node's own words.** The solution body already states the failure mode: the route view "can only display an ordering the data already supports, so if nothing in the tree encodes altitude it will draw a confident-looking line through unrelated work." Parent-child edges in an opportunity sub-tree encode subset relationships, and sibling edges encode distinct alternatives at the same level — neither encodes sequence. A tree that records what nests inside what may simply not record what comes before what, in which case any route drawn from these edges is an arbitrary ordering wearing the appearance of a plan.

That is the sharp version of the risk: the danger is not that the computation fails, it is that it succeeds and is meaningless. So the belief worth testing is not "can a chain be produced" — a chain can always be produced — but "can the computation tell the difference between a tree that encodes an ordering and one that does not, and decline in the second case."

**Why this was added rather than the existing test being rewritten.** A 2026-08-06 note on the solution recommended exactly this: add a feasibility assumption that a credible route can be computed from the tree's own edges and instrument that, "leaving the behaviour-change claim to observation of real builders." Rewriting the existing test would have changed a human-shaped question into a machine-shaped one under the old node's identity, which is the laundering the human-required lane exists to prevent. This adds a second belief instead, because the solution genuinely rests on both.

**Grounded against the repository, 2026-08-09.** No route or path module exists in `src/ost/` — the modules there are census, dedupe, frontmatter, headings, instrument, lanes, node, results, sanitize, search, sections, stranded, sweep, vault — and no route spec exists under `test/ost/` or `test/cli/`. The edge grammar this would have to read lives in `src/ost/node.ts`. So the mechanism is absent by reading, not by assumption.

⚠️ Unvalidated. Agent-ideated.
