---
type: Assumption
source: 'agent-ideation:2026-09-01-unattended-sweep'
created: '2026-09-01'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion

**Category: feasibility, with a usability edge.** Stated so it can be false: *the dated `## History` line recording when a test's lane was set is a usable proxy for when the operator first owed an answer, and the resulting order is meaningfully different from the flat one it replaces.*

Two ways this is false, and they fail in opposite directions.

It is false if the History dates are *wrong* as proxies — a test relabelled during a bulk cleanup dates from the cleanup, so a genuinely old ask reads as young and sinks in an oldest-first queue. That error flatters, which makes it the dangerous one: the queue looks like it is working.

It is also false if the History dates are *uninformative* — if the 62 were labelled in a handful of bulk passes, the derived dates cluster into a few values and the ordering they produce is nearly as flat as tree order. The mechanism would then have shipped a populated field and no signal, which is the failure the parent opportunity is about, reproduced one level up.

The first needs a person reading derived dates against git history. The second is countable from the tree, and is what the test beneath this measures.
