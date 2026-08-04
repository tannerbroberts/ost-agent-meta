---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: '0 of 10 journals overstate, and at most 2 understate by one step.'
instrument: npx vitest run test/loop/run-journal-interruption.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that a forward-written journal is accurate at the moment of interruption. The half-finished step is the interesting case and the one this handles worst: log before completion and it overstates, log after and it understates. Which failure mode occurs, and how often, decides whether the journal can be trusted.

**Risk category: feasibility.**

**Design.** Run ten passes and kill each at a randomly chosen point. For each, compare the journal's last line against what actually landed on disk and in the commit history. Count the runs where the journal claims a step that did not complete, and the runs where a completed step is missing from it.

**Why it is small.** Ten interrupted runs is an afternoon once the journal is written, and the comparison is mechanical.

**What it will not cover.** A kill is a clean interruption. A crash mid-write, a full disk, or a process killed while the filesystem is buffering are messier and may behave differently.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/loop/run-journal-interruption.test.ts — The threshold — 0 of 10 journals overstate, at most 2 understate by one step — is a mechanical comparison of the journal's last line against what landed on disk, which a spec can drive by interrupting a run at ten seeded points. It fails today because no run journal is written, so there is nothing for the spec to read.
