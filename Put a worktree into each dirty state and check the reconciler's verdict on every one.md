---
type: AssumptionTest
source: 'agent-run:autonomous-loop-2026-08-06'
created: '2026-08-06'
evidence: assertion
threshold: >-
  Every one of the eight enumerated worktree states receives a verdict, and no
  state holding uncommitted or in-progress work is classed replaceable. A single
  misclassification of that kind refutes the assumption and reconciliation loses
  to leasing.
instrument: npx vitest run test/runner/workspace-reconcile-states.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**What this measures.** Build a fixture worktree in each of the eight states the assumption enumerates — absent, valid on the expected branch, valid on another branch, uncommitted changes, detached HEAD, interrupted rebase or merge, a plain non-worktree directory, and a stale registration git still lists but which is gone from disk — and assert the reconciler returns a verdict for each, with the safe-to-reset and must-not-touch partition fixed in advance rather than read off the implementation.

**The bar, pre-committed.** Stated in the threshold above. The second half is the one that matters: total coverage of the state space is easy and says little, while never classing work-in-progress as replaceable is the property that decides whether this candidate is safe to build at all.

**Why it should be red today.** The mechanism is observably absent, not merely unwritten. `TRANSCRIPT:0f940e60-26f9-459a-ace4-5af5ce438e2b` records setup meeting exactly one of these eight states — a fixed path already occupied — and failing outright with `fatal: '/tmp/ost-main' already exists`. Setup asserts absence and has no verdict for anything else, so there is no partition for a spec to assert against.

**Honesty about that claim.** This pass could not confirm it against the code. Reads of the product directory were denied on this surface and `ost_read_repo` was not granted, so the red-today claim rests on the observed transcript rather than on the repository. The first run of this command will fail for the weaker reason — the spec file does not exist — and a builder should expect the assertions themselves to go red against today's setup path once the file is written. If they do not, the mechanism is more present than this node believes and that is worth knowing.

**What a green run does NOT settle.** It shows the partition is computable from the filesystem and that the implementation honours it. It says nothing about the case the assumption explicitly excludes: a live run mid-build leaves a worktree indistinguishable from one a dead run abandoned, and no amount of state inspection separates them. Green here is therefore compatible with reconciliation still destroying a concurrent run's work. It is also silent on desirability and cost — whether a warm shared workspace is worth this decision table at all is what the two sibling candidates exist to contest.

## Instrument Log
- 2026-08-06 **red** (exit 1) `npx vitest run test/runner/workspace-reconcile-states.test.ts` — No test files found, exiting with code 1
