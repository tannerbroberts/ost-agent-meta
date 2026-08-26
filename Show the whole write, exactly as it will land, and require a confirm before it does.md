---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[A caller shown the exact bytes will sometimes change the write before confirming]]

Every mutating call gains a preview form: it runs all the same checks, composes the exact bytes it would write, renders them, and stops. The write happens only on a second call carrying a token from the first. Nothing is written on the strength of an argument list alone.

The bet is that most regretted writes are not judgement failures but composition failures — a title that reads differently once it is a filename, a section that lands under the wrong heading, a wikilink hard-wrapped across two lines and therefore not a link at all. Those are all visible in the rendered output and invisible in the arguments.

**Compared to the alternatives.** Cheaper than a staging vault, because there is no second copy to keep in sync and no promotion step to get wrong. Weaker than a retraction layer, because it does nothing at all for a write that looked right and was wrong — it buys care at composition time, not recourse afterwards. It also taxes every good write to catch the rare bad one, which is the opposite trade from widening the refusal set.

**What would make this the wrong pick.** If the caller composing the write is the same one confirming it, the confirm is a formality and the whole cost is pure overhead. That is the assumption to test first, and it is not obviously true.

## History
- 2026-08-05 unlinked "Have five authors preview a write they were about to make and count how many change it" — moved under "A caller shown the exact bytes will sometimes change the write before confirming" — the belief this test measures now has a node of its own

## Issues
- 2026-08-26 2026-08-26 unattended sweep, repo sight held: examined for a missing instrument and deliberately left without one — recording the examination because this node carried no prior note and would otherwise be re-read from scratch every firing. The single belief beneath it, "A caller shown the exact bytes will sometimes change the write before confirming", is a claim about what a person does when shown a rendering, and its own test asks five authors to preview a write and counts how many change it. No exit code settles that: a spec can prove a preview form *renders* the bytes, which nobody doubts, but not that seeing them changes anyone's mind. The node's own prose already names the sharper version of the risk — if the caller composing the write is the same one confirming it, the confirm is a formality — and that too is answerable only by watching callers. What a human should do: set the lane with `ost-agent lane --set`, since `ost_flag_humans_required` is withheld on the unattended surface and this sweep cannot label it. Not a skipped step.
