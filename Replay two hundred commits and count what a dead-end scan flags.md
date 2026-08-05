---
type: AssumptionTest
source: 'agent-ideated:2026-08-02-maintenance-pass-2'
created: '2026-08-02'
evidence: assertion
instrument: npx vitest run test/git/dead-end-scan.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: feasibility.** Whether reversals in the artifact record can be told apart from ordinary work by a mechanism that never reads a transcript.

**The assumption under test.** That a dead end leaves a distinguishable scar. The candidate's whole case rests on it, and the obvious objection is that a repository is full of deletions, reverts, rewrites and abandoned branches that mean nothing at all — routine refactors, temp files, a rename, a squashed history. If the signature of a costly wrong turn looks identical to the signature of a Tuesday, the mechanism produces a list nobody reads.

**The test — replay on paper, no build.** Take a 200-commit window of the product repository's history. By hand or with a throwaway script, list every reversal-shaped event: a revert, a file created and deleted within one pass, a branch built and discarded, work rewritten within a day of landing, a push rejected as non-fast-forward. Then a human classifies each: **a genuine dead end that cost real time**, or **routine**.

**Pre-committed threshold, two numbers, both required.**
1. **Recall on the known case.** The 2026-07-26 duplicate build recorded on "Two agents sharing my vault can trample each other" — roughly eight hours of work discarded after a rejected push — must appear in the list. It is the single best-documented dead end this project has and the mechanism's reason for existing. If the scan misses it, the candidate closes outright, whatever the precision number says.
2. **Precision on the rest.** Of everything else flagged, **at least 1 in 4 must be judged a genuine dead end.** Below that, the operator is reading three pieces of noise per finding, and this becomes another channel producing volume without signal — which is what the parent opportunity already says about the mechanical harvester.

**The number that decides between siblings, not just about this one.** Count how many of the confirmed dead ends were *also* visible in that session's transcript. Any found here and not there is the candidate's real claim; if every one of them was in the transcript too, this mechanism is a cheaper route to the same findings rather than a route to different ones, and it should be judged on cost alone against "A model reads the raw transcript and files what the pattern scan cannot see".

**Who runs it.** A human classifies. Nothing is built and nothing is written to the tree.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/git/dead-end-scan.test.ts — Runs the dead-end scan over the recorded commit range and asserts it flags the abandoned trails and not the live ones; fails today because no scan reads dead ends off the artifact trail.
