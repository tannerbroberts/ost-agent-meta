---
type: Solution
status: shipped
source: 'agent-run:autonomous-loop-2026-07-25-pass5'
created: '2026-07-25'
evidence: assertion
---
#Solution #evidence/assertion
[[Putting the uncovered statement beside the threshold changes what a reviewer does]]

**Shipped in v0.9.0** (`ost-agent` `d9ace23`, on `main`, **not** on npm — see the root
Outcome's release note).

`ost-agent debt` now prints every **bounded** assumption test side by side: the
threshold the node pre-committed to before the run, directly above the limit the run
stated afterwards.

```text
Bounded — what each test asked for, and what its runs left out:
  Audit both vault histories for rename-shaped link breaks
      asked:     >= 2 incidents beyond the known one, else defer.
      uncovered: 2026-07-25 (refuted) — only covers rename-shaped breaks in git
                 history; says nothing about links broken by a hand edit in Obsidian
```

**Why this and not something more ambitious.** v0.8.0 made every result carry a
statement of what it did not cover, and then never read that statement — `debt`
counted the pair and stopped. A count proves a sentence exists; it cannot show the
sentence bounds anything, and a required field nobody reads is a box that gets
ticked. This is the smallest change that makes the field load-bearing: two pieces of
text the tool already held, printed together. No parsing of the result, no scoring,
no model.

**It never compares them, and the CLI says so.** Whether the run answered the
threshold printed next to it is the human call the whole coverage feature was built
around. The closing caveat was rewritten to say that rather than the older wording.

**A case the count reported as healthy and this does not.** A bounded test that never
wrote a threshold down is now named rather than skipped. A limit stated against no
stated question has nothing to be read against — the paperwork is complete and there
is nothing to check it with.

## What it found on first contact with the real vaults — 2026-07-25

The feature was run over both live trees before it was committed, and it immediately
produced a finding neither vault had recorded. Numbers from the shipped extractor,
not from a grep:

| | assumption tests | threshold extractable | contains a number or bound |
|---|---|---|---|
| ost-agent-meta | 77 | 65 | 57 |
| tetrix-ost | 27 | 27 | **4** |

In `tetrix-ost`, **21 of 27** extractable pre-commitments open with an imperative — an
*instruction to choose a threshold* — "Fix the minimum number of distinct competing players below which this
candidate is explicitly deferred", "Decide how many of the five must complete the
transfer unaided" — rather than a threshold. A test whose pre-commitment is a
reminder to pre-commit cannot come out a failure: whatever the run produces can be
read as clearing a bar nobody set.

That is filed as its own opportunity,
"My tests carry thresholds nobody ever fixed, so nothing can come out a failure",
and mirrored into the tetrix tree's root. **It is the strongest argument this feature
has** — it was built to make one sentence checkable, and the first time it read the
trees out loud it found that a quarter of one tree's tests are unfalsifiable as
written. Worth weighing against the honest case for restraint in the briefing that
named this build: nobody had yet shown the v0.8.0 field helps at all.

**What it still does not settle.** Whether printing the pair changes what a human
*does*. Finding unfixed thresholds is the tool noticing; a reviewer acting on the
notice is "Does the side-by-side change what a reviewer does about a threshold",
which is unrun. It is entirely possible the output gets skimmed like any other
report, in which case this is a nicer-looking box that still gets ticked.

**Provenance caveat.** Agent-origin, like everything else in this tree. The finding
above is a fact about two vaults inside this building, both written by the same
person and the same agent. It says nothing about whether anyone else's tree has the
same hole — see the root Outcome's standing note on external evidence.

## History
- 2026-08-05 unlinked "My tests carry thresholds nobody ever fixed, so nothing can come out a failure" — not a parent-child relation the OST hierarchy supports — every tree walk counted it as structure, so a cross-reference read as a child
- 2026-08-05 unlinked "Does the side-by-side change what a reviewer does about a threshold" — moved under "Putting the uncovered statement beside the threshold changes what a reviewer does" — the belief this test measures now has a node of its own
