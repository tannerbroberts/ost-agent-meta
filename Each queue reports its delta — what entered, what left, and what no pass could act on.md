---
type: Solution
source: 'USAGE:2026-08-05'
created: '2026-08-06'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

**The idea.** `ost_next_work` reports each bucket's movement since the previous pass, not just its contents: entered, left, and unchanged-across-N-passes. A count of 64 says nothing about whether the last pass helped; 64 with "3 left, 5 entered, 41 unchanged for six passes" says exactly what the operator wants to know.

**Why this shape.** The operator's complaint is that a pass leaves more to check than it started with, and today there is no way to tell whether that is true. The counts are absolute and each pass sees them fresh, so a pass that resolved nine items and admitted twelve is indistinguishable from one that did nothing. The unchanged-for-N figure is the one that matters most: it names the items no pass has ever been able to move, which is where the real debt is.

**How it differs from its siblings.** Diagnostic rather than corrective. It removes no item from any queue — "A shipped solution leaves the instruments queue" does that — but it is the only one that would have made the shipped-solution loop visible from outside, as four items unchanged across consecutive passes despite both being worked.

**Where it fails.** It needs a durable record of previous passes' queue contents, which the vault does not currently keep, and that record is a new thing to maintain and to get wrong. It also reports movement without judging it: a pass that empties a queue by deferring everything scores identically to one that resolved it.

⚠️ Unvalidated. Agent-ideated.
