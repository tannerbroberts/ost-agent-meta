---
type: AssumptionTest
source: 'agent-ideated:2026-08-02-maintenance-pass'
created: '2026-08-02'
evidence: assertion
instrument: npx vitest run test/ost/blind-sweep-replay.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: feasibility.** Specifically, whether the mechanism catches the failures it is being built for.

**The assumption under test.** That an all-or-nothing empty-subject guard catches a worthwhile share of real vacuous passes. The solution node already concedes the hard case against itself — the em-dash sweep that produced this branch read 302 of 306 entries, so a guard that fires only at zero subjects would have stayed silent. If total blindness is rare and partial blindness is the normal shape, this solution is a floor that costs implementation effort and buys close to nothing.

**The test (small, fast, no new code).** Take every sweep-shaped check in this vault's and OST-Agent's recorded history — the em-dash sweep, the CORS sweep, the v0.17.0 schema check, and every `ost_check` rule that iterates a node set. For each, reconstruct from git history and the health records how many times it ran and what its subject count was on each run. Classify each run: **full subject set**, **partially blind** (read some but not all), or **totally blind** (zero). One person, a few hours of git archaeology, no build.

**Pre-committed threshold.** The guard is worth building if **totally-blind runs are at least 30% of all non-full runs**. Below that, partial blindness dominates and the honest response is to close this candidate and pursue a subject-count-versus-expected assertion instead — which is a different solution and should be ideated as a sibling rather than smuggled into this one.

**What a result must also state.** How many runs could not be classified because the record does not preserve a subject count. If that number is large, the finding is not about blindness at all but about the records, and it belongs to "I can't tell what a half-finished run actually finished".

**Who runs it.** A human, from git history. This pass proposes the design only.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/ost/blind-sweep-replay.test.ts — Replays recorded sweeps and classifies each as fully blind versus partly blind; fails today because a check with an empty subject still reports a pass, so nothing distinguishes the two.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/ost/blind-sweep-replay.test.ts` — No test files found, exiting with code 1
