---
type: Solution
source: 'agent-ideation:2026-07-26-tenth-pass'
created: '2026-07-26'
evidence: assertion
---
#Solution #evidence/assertion
[[Does showing the whole sentence change what a reader does with a paste-ready command]]

**The idea.** Wherever the agent quotes a source to justify a recommendation, it renders the fragment it matched *and* the whole sentence that fragment sits in. The reader sees the elision rather than having to suspect it.

**Why this is the cheapest thing that could work.** v0.16.0 already does exactly this for one detector: an ambiguous lane declaration is reported with the full sentence, specifically because the fragment is what made it look unambiguous. Generalising that from one call site to every quoting surface is a rendering change, not a policy change — no new judgement, no new capability, nothing that could authorise anything.

**Where it fails.** A sentence is an arbitrary boundary. The qualification that changes a recommendation can sit in the *next* sentence, or in a `## Issues` annotation added months later, and this does nothing about that. It also makes output longer, and length is how the docket's paste-ready verdicts stopped being read.

⚠️ Unvalidated. Proposed by the agent that wrote the defect this responds to.
