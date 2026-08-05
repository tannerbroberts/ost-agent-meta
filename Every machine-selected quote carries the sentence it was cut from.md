---
type: Solution
source: 'agent-ideation:2026-07-26-tenth-pass'
created: '2026-07-26'
evidence: assertion
---
#Solution #evidence/assertion
[[Seeing the whole sentence changes what a reader does with the fragment]]
[[Every surface that quotes a source can be made to render the sentence, not just the one that already does]]

**The idea.** Wherever the agent quotes a source to justify a recommendation, it renders the fragment it matched *and* the whole sentence that fragment sits in. The reader sees the elision rather than having to suspect it.

**Why this is the cheapest thing that could work.** v0.16.0 already does exactly this for one detector: an ambiguous lane declaration is reported with the full sentence, specifically because the fragment is what made it look unambiguous. Generalising that from one call site to every quoting surface is a rendering change, not a policy change — no new judgement, no new capability, nothing that could authorise anything.

**Where it fails.** A sentence is an arbitrary boundary. The qualification that changes a recommendation can sit in the *next* sentence, or in a `## Issues` annotation added months later, and this does nothing about that. It also makes output longer, and length is how the docket's paste-ready verdicts stopped being read.

⚠️ Unvalidated. Proposed by the agent that wrote the defect this responds to.

## Definition of done

"Every quoting surface renders the whole sentence, not just the detector that already does"

```
npx vitest run test/ost/quote-full-sentence.test.ts
```

Green means every surface that quotes a source to justify a recommendation renders the fragment and the sentence it sits in — the generalisation this node proposes — and that a fragment straddling a sentence boundary renders every sentence it touches rather than being clipped to one. Clipping at the boundary would reintroduce, at the seam, exactly the elision the node exists to make visible.

It does not settle whether showing the sentence changes what a reader does ("Does showing the whole sentence change what a reader does with a paste-ready command"), and it does not touch this node's second stated weakness at all: the qualification that matters can sit in the next sentence or in an `## Issues` annotation added months later, and no sentence-level rendering reaches either.

## History
- 2026-08-05 unlinked "Does showing the whole sentence change what a reader does with a paste-ready command" — moved under "Seeing the whole sentence changes what a reader does with the fragment" — the belief this test measures now has a node of its own
- 2026-08-05 unlinked "Every quoting surface renders the whole sentence, not just the detector that already does" — moved under "Every surface that quotes a source can be made to render the sentence, not just the one that already does" — the belief this test measures now has a node of its own
