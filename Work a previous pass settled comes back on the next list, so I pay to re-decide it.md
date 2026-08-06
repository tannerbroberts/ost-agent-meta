---
type: Opportunity
source: 'agent-run:autonomous-loop-2026-08-06'
created: '2026-08-06'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion
[[Every work bucket excludes nodes whose own frontmatter already says they are closed]]

A pass reaches a correct decision, writes down why, and the next pass is handed the same item as outstanding work — because the bucket that selects it has no way to represent "settled by a means other than the one this bucket expects."

The need: when a pass has correctly disposed of something, I want the next pass's work list to know that, so my compute is spent on what is actually open.

## Two faces observed on the 2026-08-06 sweep

Both were established by reading the nodes the sweep offered, not inferred.

**1. `solutionsMissingInstruments` counts shipped solutions, which can never leave it.** At least 5 of the 64 listed are `status: shipped`: "A result must state what it did not cover", "Refuse a proving command whose exit code cannot report failure", "Refuse a wiki-link that contains a newline", "Refuse a write whose content is empty or literally undefined", and "Post-session transcript harvester". Two of them carry a History line from the 2026-08-05 sweep explaining the trap in the tool's own terms — a red-now instrument is *impossible* for behaviour that already ships, because a spec asserting the guard would pass on arrival, measure nothing, and hand a builder no definition of done. That pass corrected the status instead and declined to invent one. It was right, and the item came back anyway.

This is the sharpest of the two, because the bucket does not merely waste a turn: it applies pressure toward the one thing the ruleset forbids. The only action that removes a shipped solution from this list is writing a green-on-arrival instrument. A pass under budget pressure, asked every time, eventually writes one.

**2. `underservedOpportunities` counts parent opportunities whose solution space lives on their children.** "The same refusal is rediscovered every session, because nothing carries the lesson forward" reports `solutions: 0, needed: 3`. Its three candidate solutions were deliberately re-parented onto its child "A correction lives only as long as the session it was given in" by the 2026-08-05 pass, and that node says so in its own body: it "reads as underserved in `ost_next_work` for that reason — it is a parent opportunity now, not a gap." Ideating three more solutions there would undo a considered restructuring and duplicate the child's.

Of the 30 opportunities the sweep reported as underserved on 2026-08-06, roughly half are bucket categories carrying large subtrees rather than genuine gaps.

## Why this is a sibling of the evidence face, not a duplicate of it

"Evidence that fits no layer keeps coming back, so the pass never runs out of work" establishes the same trap for `unmappedEvidence`, and establishes it better — by direct test. It should not be merged with this node, because the mechanism is different and so is the fix. There, an item is mapped only when some node's frontmatter `source:` equals the evidence id, and no tool can add a `source:` to an existing node; the fix is a place to record acknowledgement that the sweep reads. Here, nothing is missing from the node at all — `status: shipped` is already on the file, and the parent-vs-gap distinction is already derivable from the child edges. The fix is the bucket's selection predicate, not a new field.

Taken together the three faces say something the individual nodes do not: this is not one gap in one bucket, it is `ost_next_work` having no general notion of "closed", so every bucket re-derives outstanding work from scratch on every pass and each one leaks in its own way.

## What it costs

The sweep's own summary is what the loop's spend ceiling is set against. Three buckets over-report, so the pass is never done, the cadence never idles, and the operator cannot use "outstanding work" as a signal for anything. The config raised the spend ceiling 8x on 2026-08-04 to unblock exactly this queue; a queue that cannot drain will absorb whatever ceiling it is given.

⚠️ Unvalidated, and agent-observed. This is the agent reporting a defect in the surface it is graded through, which is the reflexive case the Outcome warns about — the counts above are checkable by anyone re-running the sweep, and should be checked rather than taken.
