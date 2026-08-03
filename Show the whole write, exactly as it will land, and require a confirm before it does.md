---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

Every mutating call gains a preview form: it runs all the same checks, composes the exact bytes it would write, renders them, and stops. The write happens only on a second call carrying a token from the first. Nothing is written on the strength of an argument list alone.

The bet is that most regretted writes are not judgement failures but composition failures — a title that reads differently once it is a filename, a section that lands under the wrong heading, a wikilink hard-wrapped across two lines and therefore not a link at all. Those are all visible in the rendered output and invisible in the arguments.

**Compared to the alternatives.** Cheaper than a staging vault, because there is no second copy to keep in sync and no promotion step to get wrong. Weaker than a retraction layer, because it does nothing at all for a write that looked right and was wrong — it buys care at composition time, not recourse afterwards. It also taxes every good write to catch the rare bad one, which is the opposite trade from widening the refusal set.

**What would make this the wrong pick.** If the caller composing the write is the same one confirming it, the confirm is a formality and the whole cost is pure overhead. That is the assumption to test first, and it is not obviously true.
