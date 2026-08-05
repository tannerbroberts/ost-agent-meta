---
type: AssumptionTest
source: 'agent-ideated:2026-08-02-maintenance-pass'
created: '2026-08-02'
evidence: assertion
instrument: npx vitest run test/web/research-loop-provenance.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: viability.** Whether the loop's output is worth the money and the mapping attention it consumes.

**The assumption under test.** That an autonomous research loop stays tethered to the tree rather than drifting into generic reading. The solution node names this itself ("the loop can stay relevant to the tree rather than drifting"), and it is the assumption that decides the whole candidate: a loop producing plausible-but-untethered articles does not merely fail to help, it floods the inbox that [[The pass never says it is done, so I can't tell when to stop paying for compute]] already shows cannot be drained.

**The test (one shot, no loop, no schedule).** Run the derive-and-search step **once, by hand**, against the tree's current open assumptions. Produce exactly 10 candidate findings with provenance. Then have a rater who has not seen the search queries judge each finding against one question only: **does this bear on a specific named open assumption or opportunity in the tree — yes or no?** The rater is shown the finding and the tree, not the query that produced it, so relevance cannot be graded on the intent behind the search.

**Pre-committed threshold.** **6 of 10 or better** and the tether holds well enough to justify building the loop. **5 or fewer** and the candidate is closed as designed; the honest fallback is operator-initiated research on a named question, not an autonomous sweep.

**Deliberately not tested here.** Rung inflation (whether a cited web source can honestly sit above `assertion`) and unattended-web-access trust are separate assumptions and deserve separate tests — mixing them in would make a single verdict unreadable. The rung question is partly answered already by the existing `ost_rank_source` ceiling, where `expert` is the cap for a byline.

**Who runs it.** A human, or an attended session with an outward-sensing grant. This unattended pass holds no such grant and did not search.

## History
- 2026-08-05 instrument: (none) → npx vitest run test/web/research-loop-provenance.test.ts — Asserts the anti-inflation guard the node names as its first key assumption: every filed finding carries URL, retrieval date and the open assumption it was derived from, and enters at the assertion rung regardless of the host's earned standing. Red today because no research loop files anything into the inbox — web reads are operator-initiated and budgeted, never scheduled.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/web/research-loop-provenance.test.ts` — No test files found, exiting with code 1
