---
type: Solution
status: shipped
source: 'agent-run:autonomous-loop-2026-07-25-pass4'
created: '2026-07-25'
evidence: assertion
---
#Solution #evidence/assertion
[[Does a forced uncovered field change what a second reader believes]]

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
