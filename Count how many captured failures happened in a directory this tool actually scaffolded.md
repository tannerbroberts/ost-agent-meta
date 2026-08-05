---
type: AssumptionTest
source: 'TRANSCRIPT:9a406570-323c-453a-b4ca-a29b4aa01f18'
created: '2026-08-05'
evidence: assertion
threshold: >-
  At least 3 of the 4 captured exit-128 failures occurred in a directory this
  tool created; below that, a manifest cannot be the primary mechanism.
instrument: npx vitest run test/runner/scaffold-manifest-coverage.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: feasibility.**

The assumption is that the failing workspaces are ones this tool made. A manifest only exists where the scaffolder ran, so if the observed failures happened in directories a person or another tool created, the manifest is an optimisation on a fallback that has to be built anyway — and the fallback is the probe sibling, which would make this candidate redundant rather than competing.

**Design.** For each captured exit-128 failure, determine from the transcript and the directory listing it printed whether the directory was produced by this tool's scaffolder or by something else. Count. The threshold is deliberately set at the level where the answer changes the decision rather than merely being interesting.

**Why it is small.** Four sessions, each of which printed a full `ls -la` immediately before failing, so the evidence needed is already in the record.

**What it will not cover.** It says nothing about staleness, which is this candidate's real risk: a manifest is a claim about state rather than the state itself, and a reader that believes a wrong manifest proceeds confidently where a probe that finds nothing degrades to asking. That failure mode needs its own test and would want a period of real use to see, since nothing in four captured sessions could show it.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/runner/scaffold-manifest-coverage.test.ts` — No test files found, exiting with code 1
