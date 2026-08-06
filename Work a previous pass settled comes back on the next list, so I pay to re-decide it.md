---
type: Opportunity
source: 'agent-run:autonomous-loop-2026-08-06'
created: '2026-08-06'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion
[[Every work bucket excludes nodes whose own frontmatter already says they are closed]]
[[An opportunity counts as served when its subtree has solutions, not only its direct children]]
[[A disposition record every bucket consults before it lists anything]]

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

## A third face, observed by walking into it during the pass that wrote this node

The two faces above were found by reading nodes the sweep offered. This one was produced accidentally, which makes it the cleanest of the three.

This pass created "The instrument-writing step declares repo sight required and skips itself rather than inventing paths", and gave it an assumption test — "Blind-rate ten instruments for groundedness and compare against whether their pass had repo sight" — using `ost_create_node`'s `humansRequired` argument. That is the sanctioned path: the tool's own description says to use it "when a person outside the building is irreducibly the measurement", and the reason there is sound, because whether an instrument is grounded is a property of what its assertions mean against a codebase, and a missing-file red and a broken-mechanism red both exit non-zero today.

The test was created correctly, in the humans-required lane, and appears in `assumptionWork.needsHumans`. **And the solution above it immediately appeared in `solutionsMissingInstruments`, taking the count from 64 to 65.**

So a solution whose only test is *correctly* human-lane is indistinguishable, in that bucket, from one whose test is prose nobody has bothered to instrument. The bucket asks for a command, the correct answer is that no command can settle it, and giving the correct answer through the tool built for it does not register.

**Why this is the sharpest face of the three.** The other two waste a turn re-deciding something. This one penalises the right action. A pass that writes a human-lane test grows the bucket; a pass that writes a bogus command shrinks it. That gradient points away from the thing the ruleset asks for, and it points that way on every future pass, against an agent under a spend ceiling that is measured by how much outstanding work remains.

It also explains a number in the rollup that otherwise looks like neglect. Of the 65 solutions in that bucket, a large share have tests that name people as the measurement — "Five-minute orientation task on a static mock", "Test do operators get value with remote push off", "Hand-compute unblock counts and see if the operator's pick changes", and the whole commercial branch about pricing, cohorts and willingness to pay. Those are not un-instrumented through laziness. They are correctly un-instrumentable, and the bucket has no way to say so.

**What would fix this face specifically:** `solutionsMissingInstruments` should exclude a solution whose tests all carry a lane that puts them beyond compute — the same way the status filter proposed above excludes a solution that already shipped. The information is on the test's frontmatter already.

**And it compounds with a grant problem recorded elsewhere.** For a test created *before* this rule existed, the correct disposition is `ost_flag_humans_required`, which is denied on the unattended surface — twice now, in two independent firings. So the pre-existing human-lane tests cannot be labelled by the pass that finds them, and their solutions stay in this bucket permanently, where the only available action is to invent a command that cannot honestly measure them. See "The unattended run is scoped for tools nobody granted it, and it finds out one denial at a time".

_Observed directly on 2026-08-06: one `ost_create_node` call with `humansRequired`, one `ost_next_work` before and after, count 64 → 65._
