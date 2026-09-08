---
type: AssumptionTest
source: 'agent-ideation:2026-09-08-unattended-sweep'
created: '2026-09-08'
evidence: assertion
threshold: >-
  zero child processes spawned across the adapter's whole query path, on a
  fixture repo with at least one indexed symbol
instrument: npx vitest run test/product/repo-index-adapter.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.**

**Risk category: feasibility.** Whether a library-form index exists is a fact about the ecosystem, and the honest way to settle it is to try to build the thinnest adapter against one — not to survey opinions about whether such a library exists.

**What the spec must assert.** Against a fixture repository containing at least one symbol definition and one reference to it, the adapter answers "where is this defined" with the defining file and line, while `child_process.spawn` and `execFile` are stubbed to throw. Zero spawns is the bar, and it is an absolute rather than a proportion because one spawn is the whole finding: this product's CONTRIBUTING.md forbids adding a tool that shells out, so a single child process means the adoption is not an adoption.

**Why this shape of test answers the assumption rather than dodging it.** The belief is that some index can be called in-process. A survey could return a plausible name and be wrong about its distribution form; a spec that spawns nothing and still returns the right line can only pass if a library-form index genuinely exists and genuinely works. And the failure direction is informative: if no such library can be found, this spec is unpassable, which refutes the assumption and retires the candidate above it. That is the intended outcome of a refuted verdict, not a stuck test.

**Why it fails today, and what kind of red that is.** The spec file does not exist — the surface that wrote this node can read the repository but not write to it — so this is a `no-spec` red, identical under any question written on that filename, and an empty file would turn it green. It is the weak kind, recorded as such, and what carries it is the bound threshold above, which `src/eval/buildable.ts` treats as a definition of done a builder can work to when the path turns out empty. **Whoever picks this up writes the spec first**, and at that point the red becomes a red about behaviour.

**What a green here would not settle.** Whether the index is any good, whether it goes stale in a way anybody can manage, whether symbol questions dominate the string questions its sibling serves, or whether the dependency is one this project wants to carry for years. It answers one thing: that adopting is possible without a subprocess. Everything about desirability and long-run viability is untouched.
