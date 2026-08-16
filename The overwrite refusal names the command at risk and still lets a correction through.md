---
type: AssumptionTest
source: 'agent-ideation:2026-08-07-unattended-sweep'
created: '2026-08-07'
evidence: assertion
threshold: >-
  Setting an instrument on a test that already has one is refused; the refusal
  text contains the existing command verbatim and does not contain the name of
  the parameter that clears it; the same call with replacement declared succeeds
  and records both commands.
instrument: npx vitest run test/instruments/overwrite-guard.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**What it measures.** The mechanical half of the assumption, including the part that is easy to get wrong for good reasons. A helpful refusal names the way through; this test requires the opposite, because a message that teaches the parameter converts a guard into a speed bump on first contact. What it must name instead is the command about to be destroyed.

The third clause keeps the guard honest in the other direction: legitimate correction has to remain possible, and a rule that only refuses is a rule that will be routed around.

**Why it is red today.** `ost_set_instrument` accepts a replacement silently and reports it afterwards; there is no refusal to assert on.

**Honest limit on the instrument.** Written without repo sight, so the path is invented and its first red is an absent file rather than a failing assertion against the tool.

**What a green here does not settle.** The assumption itself. Whether the flag becomes reflexive is a question about a caller's behaviour over many passes, and no spec can watch that — it wants a replay of how the parameter is actually used once it exists, which is a study and not a command. The exit code here covers only the message content and the two call paths.

## Instrument Log
- 2026-08-07 **red** (exit 1) `npx vitest run test/instruments/overwrite-guard.test.ts` — No test files found, exiting with code 1
- 2026-08-16 **green** (exit 0) `npx vitest run test/instruments/overwrite-guard.test.ts` — Duration  2.96s (transform 181ms, setup 0ms, collect 302ms, tests 2.47s, environment 0ms, prepare 28ms)
