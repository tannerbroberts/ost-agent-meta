---
type: AssumptionTest
created: '2026-08-07'
evidence: assertion
threshold: >-
  Against the replayed timeline, the first rejection must arrive no later than
  30 minutes after the colliding commit lands at 02:56Z — so a cadence of at
  most 30 minutes. Measured against the eight hours actually spent, that bounds
  the loss at roughly 3.5 hours rather than 8. A cadence that only rejects at
  the final push fails.
instrument: npx vitest run test/loop/early-push-collision-window.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**What this measures.** Not whether git rejects — it does — but *when*, given a push cadence. The spec replays the recorded timeline and drives pushes at a configured interval from 00:47Z, recording the timestamp of the first rejection. The number it produces is the loss this candidate actually bounds.

The threshold deliberately does not claim the loss becomes "minutes", which is what the solution's title promises. On the recorded timeline it cannot: the pass started over two hours before anything existed to collide with, so no cadence recovers those two hours. The honest bound is time-since-the-other-commit, and 30 minutes is the bar. **If the test passes, the solution's own title is overstated and should be corrected to say what it bounds.** That is a finding worth having either way.

**Why it is red today.** No cadence-push mechanism, no replay fixture, no spec. **The caveat that weakens it:** no repository sight on this surface, so I could not verify the absence — this red is most likely a missing file rather than assertions failing against existing code.

**What a green here would NOT settle.** The blind spot this candidate never escapes: rejection needs divergent history on one branch, so two passes on separate branches, or building non-overlapping duplicates of one intent, produce no rejection at any cadence. It also says nothing about whether pushing unfinished work to a shared branch is acceptable in the repositories this would run against, which is a policy question for people.

⚠️ Unvalidated, agent-proposed. Nobody has run it.

## Instrument Log
- 2026-08-07 **red** (exit 1) `npx vitest run test/loop/early-push-collision-window.test.ts` — No test files found, exiting with code 1
- 2026-08-11 **green** (exit 0) `npx vitest run test/loop/early-push-collision-window.test.ts` — Duration  6.01s (transform 21ms, setup 0ms, collect 27ms, tests 5.80s, environment 0ms, prepare 27ms)
