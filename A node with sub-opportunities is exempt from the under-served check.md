---
type: Solution
source: 'agent-ideation:2026-08-07-unattended-sweep'
created: '2026-08-07'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Having sub-opportunities is a reliable marker of being a category]]

**The idea.** If an Opportunity has Opportunity children, it is a category, and a category is never reported as under-served. One structural fact, read off the edges, no counting.

**Why this shape.** The tree already enforces that the Outcome files categories and specific needs hang beneath them (`outcome-files-categories`). The shape is therefore known to the code, and this makes the queue read the same shape the checker does. It is the smallest possible change: a single predicate in front of the existing comparison.

**How it compares to its siblings.**
- "The under-served count rolls up through sub-opportunities" answers the same complaint with arithmetic. It is strictly more informative and strictly more fragile — it has to decide a threshold, and this does not.
- "The queue reports the leaf it wants served, never the category above it" also never reports a category, but reaches that by redirecting to the leaf rather than by falling silent. That gives the pass work; this only takes work away.

**Where it fails, stated so it can be judged.** The exemption is a false-negative machine. A category with one sub-opportunity and nothing at all beneath it is genuinely a gap, and this rule silences it forever. The tree gets quieter and no less thin, and nothing records which categories went quiet. That is the single risk worth testing before this ships, and it is what the assumption beneath it is about.

**Cost.** A predicate and fixtures. Smaller than the annotation that reported the problem.

⚠️ Unvalidated. Agent-ideated.
