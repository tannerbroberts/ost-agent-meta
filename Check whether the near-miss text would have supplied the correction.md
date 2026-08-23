---
type: AssumptionTest
source: 'agent:ideation-2026-08-03'
created: '2026-08-03'
evidence: assertion
threshold: >-
  In at least 4 of the 6 captured Edit failures, the text at the intended site
  contains everything needed to compose a correct retry.
instrument: npx vitest run test/mcp/refusal-shows-current-text.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: desirability — does one enriched failure actually resolve the question?** The candidate's claim is that a refusal carrying the current text turns a re-read-and-restart into a single corrected retry. If the old text is simply gone, there is no near-miss to show and the enriched message returns nothing useful.

**The test.** Six recorded Edit failures exist across the captured sessions — `5960b7ec`, `424486ec`, `4ff7b605`, `995b8ab1`, `0d27cebf` and `516fdfb8`. For each, recover the file state at that moment from git history, extract what the proposed message would have shown, and judge whether an agent holding that message could have composed a correct retry without re-reading the file.

**Why this test is unusually decisive for its cost.** The population is the entire known population — not a sample of six, but all six. There is no sampling error to argue about, and the whole apparatus is git history plus six transcripts.

**Why 4 of 6 rather than 5.** The two failures whose cause was a genuinely vanished target are expected to fail, and should: this candidate does not claim to fix those, "Carry a content hash from read to write and refuse on drift, naming what drifted" does. A score of exactly 4 with the two misses being drift cases is a *clean* result, not a marginal one, because it confirms the two siblings are complements rather than rivals.

**What makes the result worth acting on immediately.** This is the cheapest candidate in its row — a change to a message, no new state — and "Two thirds of my calls failed, and each one only told me after I made it" reached the same recommendation from an unrelated channel. A pass here is close to a decision.

Proposed, not run. Recording a result is a human's `ost-agent result`.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/mcp/refusal-shows-current-text.test.ts — Feeds the recorded failed edits in and asserts the refusal carries the text actually present now, and that it contains the correction; fails today because the refusal reports only that the match failed.

## Instrument Log
- 2026-08-04 **red** (exit 1) `npx vitest run test/mcp/refusal-shows-current-text.test.ts` — No test files found, exiting with code 1
- 2026-08-23 **green** (exit 0) `npx vitest run test/mcp/refusal-shows-current-text.test.ts` — Duration  554ms (transform 100ms, setup 0ms, collect 154ms, tests 93ms, environment 0ms, prepare 42ms)
