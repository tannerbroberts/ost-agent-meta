---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

Rather than teaching the caller to write shell correctly, give them something that does not require it. A comparison, a wait, a glob, a multi-line string — each gets a first-class way to be expressed that cannot be got wrong by quoting, and that way is what the surface presents. The failing form remains available and stops being the obvious thing to type.

The five identical failures in one session were all the same shape: a comparison written for one shell and evaluated by another. Nothing about the caller's intent was unclear, and nothing about it needed a shell.

**Compared to the alternatives.** Prevents the class outright rather than counting or correcting it, and it helps every caller including the first one — a repeat detector helps only from the second occurrence onward. It requires designing a new affordance per class, which is real work and does not generalise, and it can only cover the classes anyone thought to cover.

**What would make this the wrong pick.** Callers reach for shell because shell does everything. A curated set of safe forms will not cover the case in hand often enough, and each time it does not, the caller falls back to the form that fails — having now paid for both.
