---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  The deduplicated file is under 2,000 characters, or a stated expiry rule
  brings it under.
instrument: npx vitest run test/knowledge/corrections-file-size.test.ts
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that the file stays small enough to be read. A corrections file long enough to hold every lesson is one nobody opens, and there is no natural expiry — a refusal that stopped happening because the file worked looks identical to one that stopped mattering.

**Risk category: feasibility.**

**Design.** Build the file retrospectively from every refusal in the harvested transcripts and usage traces, deduplicated by class, with counts. Measure its length. Then apply candidate expiry rules — drop anything not seen in 30 days, keep only the top ten by count — and measure again.

**Why it is small.** The refusals are already captured; this is assembly and counting, with no need for anything to be running.

**What it will not cover.** Size is necessary and not sufficient. A short file may still go unread, and this measures nothing about whether a session that has it actually applies it.

## History
- 2026-08-05 instrument: (none) → npx vitest run test/knowledge/corrections-file-size.test.ts — The threshold is a measured length — "the deduplicated file is under 2,000 characters, or a stated expiry rule brings it under" — and every input already exists in the vault, so nothing here needs a person. The spec builds the corrections file from the refusals in the harvested transcripts and usage traces, deduplicates by class with counts, and asserts the assembled length; it then applies the two candidate expiry rules the node names (drop anything unseen in 30 days; keep only the top ten by count) and asserts each result against the same bound. It fails today because no builder exists — nothing in the repository assembles refusals into a corrections file, so there is no length to measure. This settles size only; the node's own limit stands, that a short file may still go unread, and this measures nothing about whether a session that has it applies it.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/knowledge/corrections-file-size.test.ts` — No test files found, exiting with code 1
- 2026-08-31 **green** (exit 0) `npx vitest run test/knowledge/corrections-file-size.test.ts` — Duration  291ms (transform 37ms, setup 0ms, collect 36ms, tests 14ms, environment 0ms, prepare 45ms)
