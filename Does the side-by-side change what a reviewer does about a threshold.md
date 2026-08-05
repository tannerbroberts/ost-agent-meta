---
type: AssumptionTest
source: 'agent-run:autonomous-loop-2026-07-25-pass5'
created: '2026-07-25'
evidence: assertion
---
#AssumptionTest #unvalidated #desirability #evidence/assertion

**Assumption under test (desirability/value).** That printing a test's pre-committed
threshold next to what its run left uncovered changes what a reviewer *does* — not
merely what they could see if they read carefully.

**Why it is the riskiest assumption under this solution.** Feasibility is settled: it
shipped, and it works on real prose in both vaults. Cost is known and small. What is
unknown is whether a report changes behaviour. The sibling
"Does a forced uncovered field change what a second reader believes" asks whether
the *statement* changes a conclusion; this asks whether the *pairing* changes an
action. Both could be no. Reports are the classic thing an operator learns to scroll
past, and this one appears inside a command that already prints two lists and a
caveat.

**Proposed test.** Take six recorded results — three where the run plainly answers
the threshold, three where it plainly answers something narrower. Show three
reviewers the pairs as `ost-agent debt` prints them, and three reviewers only the
results (today's output). Ask one question: *is this test done, or does it need
another run?*

**Pre-committed threshold:** reviewers seeing the pairing must call for another run
on at least 2 of the 3 narrow cases, and the unpaired group must call for fewer. If
both groups answer the same way, the pairing is decoration and the honest response is
to say so in the CHANGELOG rather than build further on this line.

**What it does NOT test.** Whether the threshold printed is the threshold that
mattered — a node can pre-commit to the wrong bar, and printing it faithfully makes
the wrong bar more visible, not more correct. Also untested: whether the extractor
finds the right paragraph in a tree it did not grow up on, which is a separate
feasibility question the shipped numbers only answer for two vaults inside this
building.

**Lane: humans-required.** It needs readers from outside the building, and the whole
design is that they did not run the tests themselves. Left for a person to classify
rather than flagged mechanically — the agent classifying its own feature's gate is
exactly the move the tree already worries about.

⚠️ Proposed only — the agent does not run tests or record results.
