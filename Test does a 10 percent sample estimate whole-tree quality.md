---
type: AssumptionTest
status: unvalidated
source: 'INBOX:2026-07-22-efficacy-critique.md'
created: '2026-07-25'
evidence: assertion
instrument: npx vitest run test/cli/review-sample.test.ts
---
#AssumptionTest #ported-from-ost-agent-vault #evidence/assertion

**Risk category: Viability.** Riskiest assumption: rating a small sample gives a reliable read on overall tree quality at an acceptable human cost.

**Proposed test (small, fast):** Fully rate one tree against the rubric, then compare the estimate from a 10% random sample to the full result; record reviewer time spent.

**Pre-committed success threshold:** sample estimate within ±10% of the full-tree score, at a time cost within the agreed review budget.

_Proposal only — a human runs this. Unvalidated._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 instrument: (none) → npx vitest run test/cli/review-sample.test.ts — Before a sample can estimate anything it has to be a sample. This asserts the drawing half: the review command returns 10% of the tree's reviewable nodes, the draw is stratified so every layer and every bucket is represented rather than the alphabetical head, and re-running with the same seed returns the same set while a different seed does not. A biased or unreproducible draw makes the estimate meaningless regardless of the rubric. Missing-spec red, not assertion red — no sampling command exists, so this fails on a missing file; a builder should write it against the real CLI so it goes red on the unstratified draw. It does not settle whether the sample ESTIMATES whole-tree quality, because that means scoring both the sample and the whole tree against a human-applied faithfulness rubric and comparing — a person is the measurement there and stays so.

## Instrument Log
- 2026-08-06 **red** (exit 1) `npx vitest run test/cli/review-sample.test.ts` — No test files found, exiting with code 1
