---
type: Solution
source: 'TRANSCRIPT:49d6b2d3-b867-4996-9d9d-8f10dd0871de'
created: '2026-08-07'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[The timing criteria that flake can be re-stated as operation counts without losing what they were guarding]]

The two existing candidates under this opportunity both work after the fact: report the measurement next to the criterion, or learn to read a correct firing as signal rather than noise. Both leave the ambiguity in place and help the operator resolve it faster.

This one removes the ambiguity at source. A gate that asserts "this completes in under 400ms" is measuring the machine as much as the code, and on a loaded machine it is measuring the machine almost entirely. A gate that asserts "this completes in under 12 file reads" or "in a single pass over the node set" is measuring only the code. The second cannot be failed by load, because load does not change how many reads the algorithm performs.

The move is to re-state each timing-sensitive criterion as a budget in operations — reads, writes, passes, allocations, tool calls — and to count them directly rather than inferring them from elapsed time. Where a criterion genuinely is about elapsed time as experienced by a person, it stays wall-clock and is marked as such, so that the set of gates that can flake is small, enumerated, and known.

## How it compares to the siblings

Against "A perf gate reports its measurement next to the number the criterion recorded": that makes a flake diagnosable in seconds; this makes most flakes impossible. It is more invasive — every affected criterion has to be re-expressed, and some cannot be — and it is worth less where the criterion is genuinely about human-perceived latency, which is exactly where the reporting solution is worth most. They are complements rather than rivals.

Against "Three gates fired correctly in one session and every one of them read as noise first": that addresses the operator's trust in a correct firing. This addresses the frequency of incorrect ones. If the flake rate goes to near zero, the trust problem largely dissolves on its own; if it does not, this does nothing for it.

## What it costs

Operation counting needs an instrumented seam that the wall-clock version did not — something has to count the reads. That seam is a new dependency for every gate that adopts it, and a bug in the counter is a bug in every gate at once, which is the failure mode a guard that derives its own rule already has a node for elsewhere in this tree.

## Definition of done

"A load-independent gate keeps its verdict when the machine is saturated"

npx vitest run test/gate/operation-budget.test.ts

## Issues
- 2026-08-28 2026-08-28 (unattended sweep, repo sight): DELIBERATELY NOT INSTRUMENTED, and the reason is specific rather than the standing one. This node sits in the hidden tail of `solutionsMissingInstruments` (it sorts after the 25 the sweep shows). Its `## Definition of done` names `npx vitest run test/gate/operation-budget.test.ts`, and `ost_read_repo` confirms there is no `test/gate/` directory in the repository at all — so setting that string as the instrument would produce a red that any question written on it would produce identically, which is the `no-spec` red the ruleset refuses. Not written. What the repository DOES already hold, and it is a real handoff rather than a refusal: (1) `test/telemetry/work-units-vs-elapsed.test.ts` is a green, shipped instrument for the sibling node "Assert on work units instead of milliseconds" — it defines a work unit as the files `computeNextWork` reads, asserts work units are byte-identical across repeated runs of an unchanged fixture, and pins ms-per-work-unit spread under 4x across a 32x size range; its header states that it is measured with a second untimed pass so a slow disk cannot widen the timing on the metric's own account. (2) `test/perf/contention.ts` supplies exactly the missing half — `spinners(count)` forks child processes that pin cores until killed, plus `bench`, `settle`, `median` and `spread` — and its own docstring says it exists so that tests timing real work on a deliberately busy machine do not each reinvent it. So the two halves this node's test needs (a load-independent measure, and a way to genuinely saturate the box) are both already committed and are not currently combined anywhere. A builder picking this up should write the spec that composes them — assert the gate's verdict on a fixture is unchanged between `spinners(0)` and `spinners(os.cpus().length)` — and only then is an honest red-now instrument available for the test beneath this node, "A load-independent gate keeps its verdict when the machine is saturated". Recorded here rather than as an instrument because naming an unwritten path is the failure this annotation exists to avoid; nothing was executed this pass and no rung moved.
