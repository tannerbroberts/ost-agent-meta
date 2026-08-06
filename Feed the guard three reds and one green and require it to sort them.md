---
type: AssumptionTest
source: 'agent-run:autonomous-loop-2026-08-06'
created: '2026-08-06'
evidence: assertion
threshold: >-
  The guard accepts the red-because-unbuilt command, rejects the green one, and
  declines to rule on the missing-file and broken-environment reds rather than
  accepting them — 4 of 4 classified correctly.
instrument: npx vitest run test/mcp/instrument-red-now-guard.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.**

**What this measures.** Hand `ost_set_instrument` four commands against a fixture repository and check how it classifies each exit code: a spec that fails on a real assertion about absent behaviour, a spec file that does not exist, a spec whose dependency is missing, and a spec that passes. Assert the first is accepted, the last rejected, and the middle two neither accepted nor silently treated as valid reds.

**The bar, pre-committed.** 4 of 4. Three of four is not a pass here — the middle two are the whole question, and a guard that lumps them in with real reds is the weak-instrument problem wearing an execution capability.

**Why it is red today.** Nothing executes a candidate command. `ost_set_instrument` validates the command's *shape* — it rejects shell punctuation and non-spec commands — and takes the red-now property entirely on the author's word. A spec asserting any classification behaviour fails against today's code because the classifier does not exist and neither does the execution path it would classify.

**What a green run does NOT settle.** It shows the guard can sort exit codes in a fixture where the failure modes were planted deliberately. Real repositories fail in ways nobody planted, so a green run here is weak evidence about the field. More importantly it says nothing about whether this capability should exist: executing arbitrary commands as part of a write is in direct tension with this vault's own "Append-only tool surface with no delete or shell tool", and that is a judgement about what the product is willing to be, which no spec settles and no unattended pass should decide.
