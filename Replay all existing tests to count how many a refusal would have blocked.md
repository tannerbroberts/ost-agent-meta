---
type: AssumptionTest
source: 'agent-ideated:2026-08-02-maintenance-pass'
created: '2026-08-02'
evidence: assertion
instrument: npx vitest run test/ost/unfixed-threshold-refusal-census.test.ts
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: viability** — whether the mechanism costs more than it saves, measured before it is built rather than after.

**The assumption under test.** That the threshold classifier is accurate enough at the edges to be trusted at the *write* boundary. The node states the stakes exactly: "a wrong flag costs a glance and a wrong refusal costs the whole recording." A refusal is only defensible if false refusals are rare, and nobody has counted them.

**Why this is worth running even though the node says do not build yet.** The node's sequencing — do not build until somebody has recorded a result under current rules — is about *when to build*, and it is right. This test is about *whether the thing would work at all*, it needs no build, and it can run today. If the false-refusal rate turns out to be high, the candidate can be closed now and the operator is never asked for anything.

**The test (dry run over what already exists, zero code, zero build).** Run the existing classifier from "Flag a threshold that is still an instruction to choose one" over all 91 assumption tests in this vault in **report mode**, producing the list it *would* have refused. Then a human reads that list and judges each entry against one question: **is this test's threshold genuinely not a commitment, or did the classifier misread a real pre-commitment?** Judge from the node text, blind to the classifier's reasoning.

**Pre-committed threshold.** The false-refusal rate — misread real pre-commitments as a share of everything the classifier would block — must be **at or below 5%**. At or below 5%, refusal is defensible and the candidate stays alive behind its sequencing gate. **Above 5%** and this candidate is closed: the flag version stands as the permanent answer, and the classifier stays at the read boundary where a wrong call costs a glance.

**The count that decides the rest of the argument.** However the rate comes out, the *absolute* number of tests that would be blocked matters independently. This vault has 91 tests with no results and one operator who is not running the command. If the classifier would block a large share of them, the node's own strongest objection stands on its own — hardening the one command the operator is already avoiding is optimising the wrong thing — and that conclusion does not depend on the classifier being accurate.

**Who runs it.** A human does the judging. The classifier run itself is mechanical, but a verdict here must not be recorded by compute.

## History
- 2026-08-05 instrument: (none) → npx vitest run test/ost/unfixed-threshold-refusal-census.test.ts — Replays every AssumptionTest in a vault through the unfixed-threshold classifier and counts how many filings a refusal at the `ost-agent result` write boundary would have blocked — the census that decides whether this is a guard or a wall. It fails today because the classifier is only wired to the read boundary (the flag), and no code path applies it to a result filing or reports the blocked count, so there is nothing for the spec to call.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/ost/unfixed-threshold-refusal-census.test.ts` — No test files found, exiting with code 1
- 2026-09-01 **green** (exit 0) `npx vitest run test/ost/unfixed-threshold-refusal-census.test.ts` — Duration  464ms (transform 91ms, setup 0ms, collect 144ms, tests 122ms, environment 0ms, prepare 25ms)
