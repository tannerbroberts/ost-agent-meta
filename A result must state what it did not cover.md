---
type: Solution
status: shipped
source: 'agent-run:autonomous-loop-2026-07-25-pass4'
created: '2026-07-25'
evidence: assertion
---
#Solution #evidence/assertion
[[Making a result state its gaps changes what a second reader concludes from it]]

**Shipped in v0.8.0** (`ost-agent` `d9ed3ac`, on `main`, not yet on npm).

`ost-agent result` now requires `--uncovered` alongside `--by`, and refuses a blank
one. The argument is the same in both cases: a result with no name on it cannot be
told apart from a fabricated one, and a result with **no stated limit cannot be told
apart from a complete one**. Each recording appends one line to the test's
`## Results` and one to its `## Uncovered`, in the same order, so a second run cannot
ride on the first run's limits. `debt` and `status` count the pair and name any test
whose results outrun its statements as **unbounded**.

**Where the idea came from, and why it is not a hunch.** Two compute runs on the
sibling tetrix product, two times the honest move after running a test was to *split
the node*, because the artefact left behind covered less than the threshold it was
answering. Both times that depended on an agent happening to notice. This is the
mechanical half of noticing — and it hardens the risk
[[Leave a permanent test behind instead of a one-off verdict draft]] had already
written down before that idea gets built rather than after.

**The check is deliberately shallow, and the CLI prints that it is.** It never reads
the uncovered statement or asks whether it is true; it only checks that a person was
made to write one. Whether the limit is honest stays a human judgement.

**What shipping it did NOT settle** — whether being forced to write the sentence
changes anything. It is entirely possible this produces boilerplate ("nothing much")
at the same rate as it produces insight, in which case it has added friction to the
one command humans are already reluctant to run. That is
[[Does a forced uncovered field change what a second reader believes]], and it is
unrun.

**A fix came with it.** `appendUnderSection` had been appending to the end of the
node *body* rather than the end of the named *section* — invisible while nodes had
one growing section, wrong the moment they had two. A status change after a result
would have filed itself under `## Results`.

## The reading half shipped — 2026-07-25 (v0.9.0)

This node's closing caveat said shipping the field settled nothing about whether
being made to write the sentence changes anything, because nothing ever *read* the
sentence. [[The uncovered statement printed next to what the test asked for]] is the
smallest thing that changes that: `ost-agent debt` now prints each bounded test's
pre-committed threshold directly above the limit its run stated.

**One consequence worth recording here rather than only there.** Making the pair
readable required finding the threshold in the node body, and doing that over both
live vaults produced a number neither tree had: in `tetrix-ost`, 21 of 27 assumption
tests open their pre-commitment with an imperative — an instruction to decide a
threshold, standing where the threshold should be — and only 4 of 27 carry a number. The coverage machinery
this node introduced has been enforcing a limit statement against a bar that, in that
vault, mostly does not exist. Filed as
[[My tests carry thresholds nobody ever fixed, so nothing can come out a failure]].

That is the first thing either of these two features has found on its own, and it
argues for this line of work more than any of its own reasoning did. It does not,
however, answer [[Does a forced uncovered field change what a second reader believes]],
which remains unrun.

## Issues
- 2026-08-04 `status: shipped` with no instrumented test — worth a human's attention because the combination is the one the tree has no other way to catch.

This node's only test is "Does a forced uncovered field change what a second reader believes", which names a reader as the measurement and is legitimately a human study. So the solution shipped without any command that would go red if the behaviour regressed. The mechanical half is trivially specifiable and simply was never written: a result submitted with no `## Uncovered` section should be refused, and a spec asserting that refusal would fail the day the guard is removed.

I did not add that instrument, for the reason the ruleset gives: an instrument must be red when it is written, and this behaviour already ships, so the command would pass on arrival and measure nothing. Attaching it needs to happen the other way round — as a regression spec written against the shipped guard, which is a builder's act, not this sweep's.

Same shape as the general finding recorded on "I need the tree's output to be actionable by compute alone, because my hours don't exist": a mechanism-shaped solution carrying a belief-shaped test.

## History
- 2026-08-05 unlinked [[Does a forced uncovered field change what a second reader believes]] — moved under [[Making a result state its gaps changes what a second reader concludes from it]] — the belief this test measures now has a node of its own
