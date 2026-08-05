---
type: Opportunity
source: 'USAGE:2026-08-04'
created: '2026-08-05'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion

A whole day's work goes into making tests runnable and the number of tests that have run stays at zero.

The machine-recorded trace for 2026-08-04 is 356 tool invocations, of which 88 are `ost_set_instrument` — a quarter of the day spent attaching commands to tests that already had thresholds. Against that, every bucket in the tree's own rollup reports `tested 0`. Not "tested few": zero, across 255 assumption tests, for the life of the tree.

So the pipeline has a specific shape of blockage, and it is not the one the tree keeps working on. Writing a test is cheap and happens constantly. Giving it a threshold is done. Giving it a runnable command is being done at scale. **Executing it is on nobody's surface at all** — the unattended pass is forbidden from running tests, and recording a result is a human's `ost-agent result`. Every automated hand that touches a test can only ever make it more ready to run, so readiness is the only thing that accumulates, and it accumulates forever.

The felt version, from the operator whose hours don't exist: I am paying compute to prepare work for a person who was the bottleneck in the first place. Instrumenting all 255 would leave me with 255 commands and still nothing I can point at and say it passed.

There is more than one way to address it — which is what keeps this an opportunity. Something could run instruments and record only their exit codes, without judging what a green means. The verdict step could be split so the mechanical half needs no person. Instrumenting could be rationed against the rate results actually get recorded, so readiness cannot outrun execution. Or the tree could stop counting an instrumented-but-unrun test as progress at all, and say plainly that the number that matters has not moved.

Evidence class: machine-recorded trace of tool invocations, no narrator. Declared at `assertion` because a usage trace records what this agent did with its own tools — it is not a measurement of the need, and a prior call on this same channel was correctly refused when it tried to claim otherwise. It grounds the agent-tool loop, never external demand.
