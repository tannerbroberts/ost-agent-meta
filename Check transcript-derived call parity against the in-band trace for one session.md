---
type: AssumptionTest
status: unvalidated
source: >-
  founder-directive:2026-07-24 — assertion-vs-trace distinction, stated in
  session
created: '2026-07-25'
evidence: assertion
instrument: npx vitest run test/telemetry/transcript-trace-parity.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Assumption (feasibility):** transcripts alone can reconstruct the tool-invocation record faithfully enough to be THE trace source.

**Method:** for one session driven through Claude Code with the in-band trace live, parse the transcript's tool_use blocks and compare against `.ost-agent/usage/events.jsonl`: call counts per tool, order, error outcomes. An afternoon.

**Pre-committed threshold:** >= 95% call parity with zero phantom calls. Below that, transcripts remain a supplement and the in-band trace stays canonical.

**Decides:** whether the adopt-existing lane can replace instrumentation or only enrich it.

*Proposed by the agent — to be run by a human. No results recorded here.*

## History
- 2026-08-04 instrument: (none) → npx vitest run test/telemetry/transcript-trace-parity.test.ts — Asserts the calls recovered from a session transcript match the in-band trace for the same session, which is the parity this test asks for; fails today because nothing derives calls from a transcript to compare.

## Instrument Log
- 2026-08-04 **red** (exit 1) `npx vitest run test/telemetry/transcript-trace-parity.test.ts` — No test files found, exiting with code 1
