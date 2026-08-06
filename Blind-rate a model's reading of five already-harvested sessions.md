---
type: AssumptionTest
source: 'agent-ideated:2026-08-02-maintenance-pass-2'
created: '2026-08-02'
evidence: assertion
instrument: npx vitest run test/adapters/transcript-model-reader.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: desirability.** Whether an interpretive read of a transcript produces items a human accepts as real product evidence — and whether any of them are news.

**The assumption under test.** That the conceptual friction is *in* the transcript and only the reader was wrong. This is the load-bearing claim of the candidate: the parent's census has established that a pattern scan finds nothing useful in 24 sessions, but that is equally consistent with the transcripts simply not containing the signal, in which case a more expensive reader finds nothing either and the whole branch is dead.

**The test — no build, existing corpus.** Take five sessions this vault has already harvested and still holds raw. Have a model read each end to end against a fixed question set (where did it change its mind and why; what did it abandon; where did it repeat itself; what did it believe at the start that it did not believe at the end), producing candidate items with the supporting quote attached. Strip the provenance. Hand the list to a human who was not in those sessions, mixed with a control set drawn from the mechanical harvester's output for the same sessions, and have them mark each item **real product evidence / not** and separately **new / already knew**.

**Pre-committed threshold.** **≥5 items accepted as real product evidence across the five sessions, and ≥2 of those marked new.** This is deliberately the same bar as "Hand-distil three past sessions", so the two results are directly comparable and the interpretive reader can be scored against the hand-distillation it is meant to automate. Below 5 accepted, the transcripts do not hold the signal and this candidate closes. Below 2 new, the channel adds volume without believability — the exact failure the parent opportunity was written about.

**The control set is not decoration.** If the rater accepts mechanical-harvester items at a similar rate, the interpretive read is not buying anything and the cheaper sibling wins on cost alone.

**Who runs it.** A human does the rating, blind to which items came from which reader. Reading five transcripts costs money, which is itself part of what is being decided — record the spend alongside the result.

## History
- 2026-08-05 instrument: (none) → npx vitest run test/adapters/transcript-model-reader.test.ts — Asserts the guard the node says any shipped version needs: every filed item carries a verbatim quote that is locatable in the transcript it claims to come from, so a model's interpretation cannot be laundered into observed material. Red today because the transcript adapter only pattern-scans for tool_error, retry and clarifying_question, and no model-reading path exists.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/adapters/transcript-model-reader.test.ts` — No test files found, exiting with code 1
- 2026-08-06 **green** (exit 0) `npx vitest run test/adapters/transcript-model-reader.test.ts` — Duration  476ms (transform 74ms, setup 0ms, collect 76ms, tests 11ms, environment 0ms, prepare 68ms)
