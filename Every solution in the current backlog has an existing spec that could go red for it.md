---
type: AssumptionTest
source: 'agent-ideation:2026-08-07-unattended-sweep'
created: '2026-08-07'
evidence: assertion
threshold: >-
  Across the 61 solutions currently in `solutionsMissingInstruments`, at least
  55 can be assigned an existing spec file in the product suite whose assertions
  would go red for the named behaviour without misfiling it. Fewer than 55
  refutes the rule and argues for the escape hatch becoming the default.
instrument: npx vitest run test/instruments/spec-path-resolution.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**What it measures.** Whether the refusal is livable at the scale the tree actually has. The bar is a census over the real backlog rather than a fixture, because the question is empirical: it is about this repository's spec layout, not about the rule's logic.

The spec form is the mechanical half — that the tool resolves a path against the configured repo, refuses an absent one, and names the escape in its message. The census half is what decides the assumption, and a builder running this should record the census number in the result even though the exit code only covers the resolution.

**Why it is red today.** `ost_set_instrument` accepts any spec-shaped string without resolving it, which is how every instrument in this tree came to name a file that does not exist.

**Honest limit on the instrument.** Written without repo sight, so the path is invented; its first red is an absent file. The irony is load-bearing rather than incidental — this is a blind instrument for the rule that would forbid blind instruments, and it is exactly the artefact "An instrument records whether the pass that wrote it could see the repository" wants marked.

**What a green here does not settle.** The census. A passing resolution check says the guard works; it says nothing about whether 55 of 61 solutions have a home, and that number is the assumption.

## Instrument Log
- 2026-08-07 **red** (exit 1) `npx vitest run test/instruments/spec-path-resolution.test.ts` — No test files found, exiting with code 1
