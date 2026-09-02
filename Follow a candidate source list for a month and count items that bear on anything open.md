---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: At least 5 items in the month bear on an open assumption or opportunity.
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that a small subscription list produces a worthwhile hit rate. Most arrivals will bear on nothing; the question is whether enough bear on something to justify the reading.

**Risk category: viability.** Whether the attention spent is repaid.

**Design.** Name the five or six sources that would go on the list. Follow them for a month without building anything, and for each item that arrives, record whether it bears on an open assumption or opportunity in this tree. Count hits against total volume.

**Why it is small.** No code, no integration — reading a handful of feeds for four weeks and keeping a tally.

**What it will not cover.** The list is chosen by the person whose blind spots are the problem, and a month is short. It also measures relevance as judged by the same person, immediately, which will undercount things that turn out to matter later.

A human runs this and records the result.

## 2026-09-02 unattended sweep — examined for an instrument, and it cannot take one

Recorded here so no future pass re-derives it. This test was one of the four remaining genuinely-unexamined entries named in the residue on "The biggest queue on my report is one the surface reading it to me has no tool to clear".

**Verdict: not repo-answerable, and this is the least ambiguous of the four.** The threshold is "At least 5 items in the month bear on an open assumption or opportunity", and the predicate "bears on something open" is a person's judgement of relevance made against a tree they already hold in their head. The body says so outright — "A human runs this and records the result" — and its own limits paragraph notes the same person both chooses the sources and judges the hits. Neither half of that is reachable by an exit code, and the four weeks of following are wall-clock besides.

**What the repair is, and why this pass cannot make it.** A person is the measurement and the frontmatter carries no lane saying so, so this test is in neither the ask queue nor any labelled count. `ost_flag_humans_required` is withheld from the unattended surface by design; the fix is one `ost-agent lane --set` naming this test humans-required.

_Nothing was executed, no instrument set, no lane set, no rung moved, no status changed. Read first-party from disk during the 2026-09-02 unattended sweep._
