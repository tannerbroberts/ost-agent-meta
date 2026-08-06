---
type: AssumptionTest
source: 'agent-run:autonomous-loop-2026-08-06'
created: '2026-08-06'
evidence: assertion
threshold: >-
  Every solution with status shipped or deferred is absent from
  solutionsMissingInstruments, and every unvalidated solution lacking an
  instrument is still present — no exceptions in either direction.
instrument: npx vitest run test/ost/next-work-status-filter.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.** A fixture vault with four solutions — one `shipped` without an instrument, one `deferred` without one, one `unvalidated` without one, one `unvalidated` with one — run through `computeNextWork`. The bucket must contain exactly the third.

**Why it is red today.** This is not merely a missing file. The assertion it makes about current behaviour was checked directly on the 2026-08-06 sweep: `solutionsMissingInstruments` listed "A result must state what it did not cover", "Refuse a proving command whose exit code cannot report failure", "Refuse a wiki-link that contains a newline", "Refuse a write whose content is empty or literally undefined" and "Post-session transcript harvester", and all five carry `status: shipped` in their own frontmatter. The predicate does not consult status. A spec asserting that it does fails against today's code for that reason, not only because the file is absent.

**What a green run does not settle.** It proves the filter reads the field. It says nothing about whether the field is *true* — whether those five are really built. That is the whole risk this candidate carries and it is deliberately outside this instrument, because no spec can check a status claim against a repository the sweep cannot read. The sibling test "Audit every shipped solution against the repository before trusting the exclusion" is where that lives, and it needs a person or a granted repo path. It also settles nothing about desirability or usability: a correct filter that nobody wanted is still correct.

## Instrument Log
- 2026-08-06 **red** (exit 1) `npx vitest run test/ost/next-work-status-filter.test.ts` — No test files found, exiting with code 1
