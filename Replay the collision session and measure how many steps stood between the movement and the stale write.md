---
type: AssumptionTest
source: 'TRANSCRIPT:424486ec-3489-4b53-8e2b-012232d221ab'
created: '2026-08-06'
evidence: assertion
threshold: >-
  In at least 3 of the recorded collision sessions, two or more run steps
  separate the first detectable movement from the first act on stale content.
  Fewer than that and a between-steps sentinel is sampling into a window too
  narrow to help.
instrument: npx vitest run test/runner/drift-sentinel-window.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.** This measures a distance in recorded transcripts. Nobody has to be interviewed and nothing has to be built first — the sessions already exist in the evidence channel, and the step ordering inside them is what the spec reads.

**What the command does.** Loads the captured sessions that contain a failed string match, reconstructs for each the step at which the ground first moved (HEAD change, or a read file's mtime advancing) and the step at which the run first read or wrote stale content, and asserts the distribution has enough room in it for sampling to fire.

**Why it is red today.** `test/runner/drift-sentinel-window.test.ts` does not exist, and neither does the replay helper it would need. This is a missing-file red rather than an assertion red — the honest weaker of the two — because the product repository could not be read from this surface: reads of it were denied, which is recorded on its own opportunity. A builder should expect to write the replay helper before the assertion means anything.

**What a green here does NOT settle.** It says a sentinel would have had time to fire. It says nothing about whether firing helps: an interrupted unattended run that then has no authority to decide what to do about the interruption may be worse off than one that failed at the write. It also says nothing about the false-stop rate, which belongs to the preflight candidate, and nothing at all about desirability — no operator outside this vault has said any of this matters.

## Instrument Log
- 2026-08-06 **red** (exit 1) `npx vitest run test/runner/drift-sentinel-window.test.ts` — No test files found, exiting with code 1
