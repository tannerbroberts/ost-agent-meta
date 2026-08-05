---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A curated set of safe forms covers enough of what callers actually need]]

Rather than teaching the caller to write shell correctly, give them something that does not require it. A comparison, a wait, a glob, a multi-line string — each gets a first-class way to be expressed that cannot be got wrong by quoting, and that way is what the surface presents. The failing form remains available and stops being the obvious thing to type.

The five identical failures in one session were all the same shape: a comparison written for one shell and evaluated by another. Nothing about the caller's intent was unclear, and nothing about it needed a shell.

**Compared to the alternatives.** Prevents the class outright rather than counting or correcting it, and it helps every caller including the first one — a repeat detector helps only from the second occurrence onward. It requires designing a new affordance per class, which is real work and does not generalise, and it can only cover the classes anyone thought to cover.

**What would make this the wrong pick.** Callers reach for shell because shell does everything. A curated set of safe forms will not cover the case in hand often enough, and each time it does not, the caller falls back to the form that fails — having now paid for both.

## Definition of done

"Count how many of the harvested shell failures a curated set of safe forms would have covered"

```
npx vitest run test/knowledge/safe-form-coverage.test.ts
```

Green means a named candidate set of first-class forms — comparison, wait, glob, multi-line text, pipeline — fully expresses at least 60% of every shell command in the harvested corpus and at least 80% of the *failing* ones. Both bars are the node's own. It is red today because no candidate form set exists in the repository and nothing classifies the corpus against one.

**Why coverage is the whole question.** Callers reach for shell because shell does everything. If the safe forms miss the case in hand often, the caller falls back to the failing form having now paid for both — which is strictly worse than not offering the forms at all. The two weights matter separately: covering most commands while missing most *failures* would be a set that is popular and useless, and a single blended number would hide it.

**The corpus this scores against is now enumerated.** "I repeat one shell mistake five times in a session, because the first failure never said it was a class" carries a hand-sort of the harvested failures into five classes, of which three are one underlying class — commands composed for bash and run under zsh. That table is the raw material for naming the candidate forms, and it is also a warning about this command's denominator: it is a sort by the pass that read the records, not a mechanical one.

**What green does NOT settle.** Past commands were written by someone who had only shell available and shaped their intent around it. What a caller would write with better forms available is not visible in this corpus at all, so high coverage of past commands is weak evidence about future ones — and low coverage would be the more trustworthy result of the two.

## History
- 2026-08-05 unlinked "Count how many of the harvested shell failures a curated set of safe forms would have covered" — moved under "A curated set of safe forms covers enough of what callers actually need" — the belief this test measures now has a node of its own
