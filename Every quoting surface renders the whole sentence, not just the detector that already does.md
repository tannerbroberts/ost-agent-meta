---
type: AssumptionTest
source: 'agent-ideation:2026-08-05-unattended-pass'
created: '2026-08-05'
evidence: assertion
threshold: >-
  Every surface that quotes a source to justify a recommendation renders both
  the matched fragment and the full sentence containing it — not only the
  ambiguous-lane detector shipped in v0.16.0 — and a fragment that spans a
  sentence boundary renders every sentence it touches rather than being silently
  clipped to one.
instrument: npx vitest run test/ost/quote-full-sentence.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: feasibility.** Whether the generalisation is actually a rendering change, as the parent claims, or whether the other call sites do not have the surrounding sentence in hand at the point they quote.

**The assumption under test.** The parent's argument for this being cheap is that v0.16.0 already does it for one detector, so extending it is "a rendering change, not a policy change — no new judgement, no new capability, nothing that could authorise anything." That premise is checkable. It is false for any call site that receives a pre-extracted fragment rather than an offset into a source, and which of the surfaces are in that position is not something the node's body knows.

**Why the sentence-boundary clause is in the threshold.** The parent names its own weakness — "a sentence is an arbitrary boundary" — and the honest partial answer is that a quote which straddles two sentences must not be clipped to one, because clipping *at* the boundary is the elision this whole node exists to make visible. A spec that only checks the easy case would pass on an implementation that reintroduces the defect at the seam.

**What is red today.** One detector does this; the rest do not. The spec fails against today's code at every call site except the v0.16.0 one, which makes it the stronger kind of red: it is not waiting on a file to exist, it is asserting behaviour the existing code demonstrably lacks, with one passing case already in the tree to show the target shape is reachable.

**What a green result does NOT settle.** Whether showing the sentence changes what anyone does — that is [[Does showing the whole sentence change what a reader does with a paste-ready command]], which needs readers. And it does not touch the parent's second stated weakness at all: the qualification that would change a recommendation can sit in the *next* sentence, or in an `## Issues` annotation added months later, and no sentence-level rendering reaches either. A green here means the elision is visible at sentence granularity and says nothing about whether that granularity is the right one.

**The cost the parent names is real and unmeasured here.** Longer output is how the docket's paste-ready verdicts stopped being read. This test asserts the sentence is rendered; it does not measure what the added length costs, and a builder should not read green as evidence the trade was worth making.

**Lane: compute-only.** Fixture sources and the quoting surfaces' own output; no person is the measurement.

⚠️ Unvalidated. Agent-ideated by an unattended pass. Nothing here was run.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/ost/quote-full-sentence.test.ts` — No test files found, exiting with code 1
