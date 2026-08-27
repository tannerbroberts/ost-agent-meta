---
type: AssumptionTest
source: 'agent-run:unattended-sweep-2026-08-27'
created: '2026-08-27'
evidence: assertion
threshold: at least 20 of the 25 members on the second call are absent from the first
instrument: npx vitest run test/mcp/window-advances-per-firing.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.**

Seed a vault with more unmapped evidence than the cap — the fixture idiom in "test/mcp/large-tree.test.ts" already builds 500 nodes this way, via `initVault` + `buildPassContext` + a `createNode` loop. Call `computeNextWork` twice against the unchanged vault, stamping per firing rather than per call. Compare the ids in `unmappedEvidence` across the two.

Today the two calls return an identical list, because selection is an ascending sort truncated at the head with nothing recording that a member was served. That is the failure this test is written to catch, and it is the observed behavior this whole branch rests on.

**This instrument is a no-spec red, and that is a property of the surface rather than a choice.** The strong form of this command is `npx vitest run test/mcp/next-work.test.ts` with a `-t` selector naming the assertion, so that it fails inside a 16KB file of live specs for a reason specific to this question. `ost_set_instrument` and `ost_create_node` both refuse that: the quoted selector reads as shell punctuation, and the refusal message says so. The tool's own description offers `-t "refuses a write whose base hash drifted from the last read"` as its example of a *strong* instrument, so the documented best form is one the validator will not accept. With only a bare filename expressible, the sole way to be red about behaviour that does not exist yet is to name a file that does not exist yet — which is the vacuous red the ruleset condemns. Recorded here rather than worked around; see the hygiene note this pass left on "My instruments are red because a file is absent, not because the behaviour is".

The path was chosen with repo sight (`test/mcp/` listed on 2026-08-27, 29 files, none by this name), so it is a deliberately new spec rather than a guess at an existing one.

**What this test does not settle.** It measures only that the window moves. Nothing about whether it moves at a useful rate, nothing about whether the items it surfaces are worth the firing's attention, and nothing about desirability, viability or usability — a green here proves the carousel turns, not that anyone is better off for it. It also does not by itself settle the call-versus-firing hazard in the parent assumption: a spec that calls `computeNextWork` twice in one process would go green on exactly the behaviour that would make the mechanism useless in production, so the spec must stamp per firing and assert that too.
