---
type: AssumptionTest
created: '2026-08-07'
evidence: assertion
threshold: >-
  Replay the recorded timeline against a scan run at start-of-build. It must
  report the collision. If it cannot — because the other commit did not exist
  yet at 00:47Z — the test fails as specified, and the recorded failure is the
  finding: the scan must run on a cadence, not once, and the solution needs
  re-specifying before it is built.
instrument: npx vitest run test/loop/prior-art-scan-catches-recorded-collision.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**What this measures.** Whether the detector this solution proposes fires on the one collision the tree has actually observed. The spec builds a repository fixture reproducing the recorded timeline — clone clean at 00:47Z, the other session's commit landing at 02:56Z, the build committing at 08:46Z — and runs the start-of-build scan at 00:47Z against it.

**This test is expected to fail on its merits, and that is why it is worth writing.** The assumption above states the doubt plainly: the prior art did not exist when the pass started, so a single scan at start-of-build sees nothing. A failure here is not a broken test, it is the measurement — it says the candidate as worded cannot work and must become a scan on a cadence, which materially changes what it costs and how much it differs from its early-push sibling. Writing the test to pass by scanning at some later, chosen moment would beg the question; the scan time is fixed at start-of-build deliberately.

**Why it is red today.** No scan exists and no fixture exists. **The weakening caveat:** with no repository sight on this surface I could not confirm no such spec is already present, so this red is an absent file rather than assertions failing against real code.

**What a green here would NOT settle.** That the scan catches collisions in general. The node this sits under records the sharper case explicitly — two passes building non-overlapping duplicates of one intent leave nothing textual to find, and no version of this scan sees them. It would also say nothing about false positives, which is the cost side: a scan that stops a pass whenever recent history looks vaguely related is worse than no scan.

⚠️ Unvalidated, agent-proposed. Nobody has run it.

## Instrument Log
- 2026-08-07 **red** (exit 1) `npx vitest run test/loop/prior-art-scan-catches-recorded-collision.test.ts` — No test files found, exiting with code 1
