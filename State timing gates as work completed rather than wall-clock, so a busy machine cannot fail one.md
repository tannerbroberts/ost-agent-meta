---
type: Solution
source: 'TRANSCRIPT:49d6b2d3-b867-4996-9d9d-8f10dd0871de'
created: '2026-08-07'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

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
