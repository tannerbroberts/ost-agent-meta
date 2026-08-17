---
type: AssumptionTest
source: 'agent-run:autonomous-loop-2026-08-06'
created: '2026-08-06'
evidence: assertion
threshold: >-
  The 65 real records collapse to at most 8 clusters covering at least 90% of
  events, AND every signature occurring exactly once is still listed
  individually rather than folded into a remainder.
instrument: npx vitest run test/adapters/friction-signature-clustering.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Who runs it.** An attended session with a build environment, or a human. This pass could not set a lane label — that is a human's `ost-agent lane --set`.

**What this measures.** Run the signature function over the 65 transcript records already in this vault — real corpus, not a fixture — and assert both halves of the tension at once: that it actually reduces, and that it does not bury the rare event. The specific canary is session `2a4bcf6e`'s lone `clarifying_question`, an unattended firing stopping to ask a human which of three ways to proceed; the spec names it and requires it to appear as its own listed entry.

**The bar, pre-committed.** At most 8 clusters over ≥90% of events, and every singleton signature individually listed. Both, or the signature is wrong and should be re-cut rather than tuned — a rule that reduces by hiding is worse than no rule.

**Why it is red today.** The harvester emits one record per session with no signature computed anywhere; this pass's queue is the proof, showing 65 items whose only grouping is the session id they came from. The spec fails against an absent function, and its corpus assertions fail against the live emission shape rather than against a file nobody wrote.

**What a green run does NOT settle.** It shows one signature works on the 65 records this vault has produced so far, all from one agent doing one kind of work. Another operator's frictions will not look like these, so this is evidence about a corpus and not about the rule. It also cannot tell whether a count is what the operator wanted from self-observation in the first place — the tidy queue might be worse than the diary, and only a person can say.

## History
- 2026-08-06 body edited — The body declared "Lane: compute-only", which this pass had no power to set — `ost_flag_humans_required` is withheld on this surface and only a human's `ost-agent lane --set` moves what compute may run. The node carries no `lane:` field, so its effective lane is needs-humans (confirmed: it landed in `assumptionWork.needsHumans`), and the prose contradicted that. Replaced with the vault's established "Who runs it" phrasing.

## Instrument Log
- 2026-08-06 **red** (exit 1) `npx vitest run test/adapters/friction-signature-clustering.test.ts` — No test files found, exiting with code 1
- 2026-08-17 **green** (exit 0) `npx vitest run test/adapters/friction-signature-clustering.test.ts` — Duration  520ms (transform 26ms, setup 0ms, collect 31ms, tests 5ms, environment 0ms, prepare 49ms)
