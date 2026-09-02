---
type: AssumptionTest
source: 'agent-ideation:2026-08-07-unattended-sweep'
created: '2026-08-07'
evidence: assertion
threshold: >-
  Against a fixture of real event strings drawn from this vault's corpus, a
  single normaliser yields exactly one group for the `File has not been read
  yet` family across differing paths and sessions, and three distinct groups for
  the permission denials naming `ost_check`, `ost_debt` and `ost_read_repo`.
instrument: npx vitest run test/adapters/friction-signature.test.ts
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**What it measures.** Whether one normalisation setting can satisfy both directions at once. The two halves pull opposite ways — the first rewards stripping identifiers, the second punishes it — so a normaliser that passes both exists only if tool identity and payload identity can be separated. The test is designed so that the easy answers fail: strip everything and the second assertion breaks, strip nothing and the first does.

The fixture strings are taken from the corpus rather than invented, which is the only part of this that is grounded in anything.

**Why it is red today.** Ingest performs no grouping at all; every event becomes its own item, so the first assertion fails.

**Honest limit on the instrument.** Written blind — no repo sight on this surface — so the named path does not exist and its first red is an absent file rather than a failing assertion against the ingest adapter.

**What a green here does not settle.** That the four groups it produces correspond to four *needs*. Grouping identical refusals is a claim about strings; the parent opportunity's claim is about needs, and nothing here bridges that.

## Instrument Log
- 2026-08-07 **red** (exit 1) `npx vitest run test/adapters/friction-signature.test.ts` — No test files found, exiting with code 1
- 2026-09-02 **green** (exit 0) `npx vitest run test/adapters/friction-signature.test.ts` — Duration  265ms (transform 36ms, setup 0ms, collect 40ms, tests 4ms, environment 0ms, prepare 24ms) [spec daa4db2bda62]
