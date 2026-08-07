---
type: AssumptionTest
created: '2026-08-07'
evidence: assertion
threshold: >-
  Given the briefing paragraph both colliding sessions read, two independent
  readings must produce work identities that a claim matcher resolves to the
  same item. The bar is that the matcher returns "already claimed" — not that
  the two strings are equal. Anything less than a match on this paragraph fails,
  because this is the one case known to have collided.
instrument: npx vitest run test/loop/work-claim-vocabulary-match.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**What this measures.** Whether a claim can be matched at all. The spec fixes the briefing paragraph from the 2026-07-26 collision, takes two differently-worded namings of the work it describes — at minimum the two the colliding sessions' commits imply, "invited-visitor arm split" and "add an arm column to visitor_events" — writes a claim from the first, and requires the matcher to refuse the second as already claimed.

The matcher is the object under test, not the file format. A spec that asserts a claim file can be written and read back would pass on a mechanism that never excludes anything, which is precisely the failure this assumption exists to catch.

**Why it is red today.** No claim mechanism and no matcher exist — this solution was created in this pass. The fixture paragraph is not in the repository either, so a builder writing this will build the fixture as part of it. **Stated because it weakens the instrument:** this surface has no repository sight (`product.repos` unconfigured, direct reads of the product directory denied), so the red is an absent file rather than assertions failing against a module that exists. A builder should expect to write the mechanism, not repair one.

**What a green here would NOT settle.** Only that two namings of one paragraph match. It would not show that a claim survives a pass dying mid-build — the expiry problem the solution's own body names as inherited and unsolved — nor that two passes would bother to claim before starting, nor that the vocabulary generalises past this one paragraph. n=1 on the input, and the 1 is the case selected because it is the case that failed.

⚠️ Unvalidated, agent-proposed. Nobody has run it.

## Instrument Log
- 2026-08-07 **red** (exit 1) `npx vitest run test/loop/work-claim-vocabulary-match.test.ts` — No test files found, exiting with code 1
- 2026-08-07 **green** (exit 0) `npx vitest run test/loop/work-claim-vocabulary-match.test.ts` — Duration  408ms (transform 26ms, setup 0ms, collect 28ms, tests 179ms, environment 0ms, prepare 24ms)
