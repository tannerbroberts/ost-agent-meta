---
type: AssumptionTest
source: 'TRANSCRIPT:785ea509-96b9-4225-b45a-babd5321aafc'
created: '2026-08-05'
evidence: assertion
threshold: >-
  At most 5 distinct consumers read a suite result, and every one can be
  migrated in a single change.
instrument: npx vitest run test/runner/suite-result-consumer-census.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: feasibility.**

The assumption is that the migration is bounded. This candidate's cost is not building the richer result — it is that every consumer has to be taught to read it, and the ones that are not taught keep reading the boolean and become *more* wrong than before, because now an exclusion set exists and they are ignoring it. A partial rollout is worse than none, so the question that decides whether to start is how many places must change together.

**Design.** Enumerate every place that consumes a suite verdict — the gate, the instrument log, the loop's own build check, CI, and anything reading an exit code as a coverage claim. For each, determine whether it can be migrated independently or only in lockstep with the others. Count both numbers.

**Why it is small.** A census over committed code, no build.

**Why this is the right thing to measure first.** The vault has already paid this cost once: [[When the rules tighten, my existing tree is stranded out of compliance]] records what happens when a stricter reading arrives after the artifacts it judges. Sizing it in advance is the cheap version of that lesson.

**What it will not cover.** It counts consumers, not the cases they would newly catch. The strongest argument for this candidate is that it also catches *undeclared* shortfalls — a test file that failed to collect, a filter typo that silently matched nothing, a suite that exited early — and none of those appear in a consumer census. Sizing that upside needs a separate replay over past runs.
