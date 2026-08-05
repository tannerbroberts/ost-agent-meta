---
type: Solution
created: '2026-08-05'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Check the accepted grammar is retrievable without submitting anything, and names every rejected construct]]

**The mechanism: make the constraint readable instead of discoverable-by-violation.** The surface exposes what it accepts — the dialect, the forbidden constructs, the shape of a valid artifact — at an address a composer can read before it writes a line. The rule that scripts are plain JavaScript and that type annotations, interfaces and generics are the usual way to get it wrong is currently held only inside the parser's error message, which means the only way to obtain it is to be wrong first.

**Why this shape.** It is the cheapest of the three and the only one that costs nothing at composition time. The information already exists and is already well-written — the refusal message names the cause and lists the common violations — so this is a relocation, not an authoring job.

**Compared to its siblings.** The most general: one published grammar serves every composer, every artifact size, and every future surface that adopts the pattern, while incremental validation and a starter skeleton each have to be built per surface. It is also the weakest guarantee of the three, and the weakness is the familiar one — published documentation only helps a composer who reads it, and a composer confident it knows the dialect will not go looking. That is the same bet the corrections-ledger candidate under a neighbouring opportunity makes, and it fails the same way.

**What would make this the wrong pick.** If the composer's error is confident rather than ignorant. Writing TypeScript into a JavaScript-only file is not usually a gap in knowledge — it is a habit, and habits do not consult references. Against a confident composer, the skeleton sibling wins because it does not require anyone to look anything up.

⚠️ Unvalidated. Agent-ideated on 2026-08-05 from two machine-captured rejections at lines 24 and 172.
