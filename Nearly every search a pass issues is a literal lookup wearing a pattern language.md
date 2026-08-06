---
type: Assumption
status: unvalidated
source: 'TRANSCRIPT:8a9777ad-a1ca-47fc-ab8e-3bd4b001a5cd'
created: '2026-08-06'
evidence: observed
---
#Assumption #unvalidated #evidence/observed
[[Census the recorded searches and split them by whether their argument came from the tree]]

**Feasibility, and a scope claim rather than a technical one.** A literal-only interface eliminates this failure class only if it covers the work. If passes routinely need real pattern semantics over node text, the calls move to whatever escape hatch exists and the failures return through it, having cost a new interface on the way.

Stated so it can be false: a small minority of a pass's searches need pattern matching. It is false if passes commonly search for shapes rather than strings — headings by prefix, wikilinks by bracket structure, frontmatter fields by position. This pass did exactly that twice within an hour, matching `^\s*-?\s*\[\[` and `\[\[` to find child edges, and neither is a literal lookup.

That is uncomfortable evidence against the assumption and it should be weighed honestly rather than explained away. Two counts out of a few dozen is still a minority, but they were not incidental — finding a node's children was the single most load-bearing search of the pass, and it needed structure.

The saving distinction, if there is one: those patterns were written by hand and contained no tree text. The failures this opportunity is about all came from *interpolating* node content into a pattern. So the assumption that matters may be narrower and more defensible — that searches whose argument comes from the tree are almost always literal, while searches over document structure are almost always hand-written and safe. If the census below supports that split, the interface should be drawn along it rather than around literalness in general.

Which would make this a better solution than its current title describes, and the honest outcome of the test may be a rewrite rather than a verdict.
