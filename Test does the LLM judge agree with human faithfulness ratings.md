---
type: AssumptionTest
status: unvalidated
source: 'INBOX:2026-07-22-efficacy-critique.md'
created: '2026-07-25'
evidence: assertion
instrument: npx vitest run test/eval/faithfulness-judge.test.ts
---
#AssumptionTest #ported-from-ost-agent-vault #evidence/assertion

**Risk category: Feasibility.** Riskiest assumption: an independent LLM judge's faithfulness ratings correlate well enough with human judgment to be trusted as a quality signal.

**Proposed test (small, fast):** Have the judge and 2–3 humans independently rate the same ~30 nodes for grounding/shape; measure inter-rater agreement.

**Pre-committed success threshold:** judge-vs-human agreement ≥0.7 (e.g. Cohen's/weighted kappa) with no systematic bias.

_Proposal only — a human runs this. Unvalidated._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 instrument: (none) → npx vitest run test/eval/faithfulness-judge.test.ts — Agreement with human ratings can only be measured if the judge emits something comparable to them, and today there is no judge and no scale to compare on. This asserts that half: the judge returns a faithfulness score on a fixed scale for every node it is given, cites the specific evidence span it scored against, and is deterministic enough that the same node scored twice lands within one point — an unstable or uncited score cannot be compared to a human rating at all. Missing-spec red, not assertion red: the pass cannot read the repo, so the command fails on a missing file; a builder should write it against the real judge call so it goes red on the uncited score. It does not settle agreement with humans, because that requires human faithfulness ratings to exist as ground truth, and producing those is a person's work.

## Instrument Log
- 2026-08-06 **red** (exit 1) `npx vitest run test/eval/faithfulness-judge.test.ts` — No test files found, exiting with code 1
