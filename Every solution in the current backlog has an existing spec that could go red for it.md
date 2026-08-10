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

## The census half now has a denominator — read from the repository, 2026-08-10

**No test was run and nothing here clears a gate.** This node's own text says the census half is what decides the assumption and that the exit code only covers path resolution. The census still has not been done. What this pass could do, with repo sight the author did not have, is measure the population the census would run against — and that alone bears on the threshold.

**The product suite, listed directory by directory.** Seventeen of the twenty directories under `test/` were enumerated (`automation`, `fixtures` and `processes` were not, and no instrument names them). They hold roughly **184 spec files**, the largest being `test/mcp` (26), `test/security` (22), `test/ost` (21) and `test/release` (18).

**Against that, this vault carries 277 `instrument:` fields naming 277 distinct paths, of which 27 resolve.** So the backlog is not asking to be reassigned across a suite with room for it — it is asking for more distinct spec files than the entire suite currently contains, by half again.

**Why that is not yet a refutation, and I want to be precise about it.** This node's threshold is *"at least 55 of 61 can be assigned an existing spec file whose assertions would go red for the named behaviour without misfiling it."* Assignment is many-to-one: several backlog solutions could legitimately land in one existing spec, and 184 files is not obviously too few homes for 61 solutions. The count above refutes a different and easier claim — that the tree's *current* instrument paths are mostly assignable — and that claim is not this one. Read it as sizing, not as a verdict.

**What it does establish, and it is the part worth carrying.** The gap between 27 resolving and 277 named is not a backlog of files waiting to be written into a settled layout. Seventeen of the unresolved paths name one of seven directories that do not exist in the suite at all — `test/instruments/`, `test/preflight/`, `test/tools/`, `test/guards/`, `test/evidence/`, `test/gate/`, `test/rank/` — and `test/instruments/spec-path-resolution.test.ts`, this node's own instrument, is one of them. So the escape hatch this node's threshold contemplates is load-bearing for at least those seventeen, because there is no existing spec to resolve them against and the rule as stated would refuse every one.

**What a builder should record if they run the census.** Two numbers, not one: how many of the backlog solutions get an existing home, and how many of those homes are the *same* file. A census reporting 55 of 61 assignable would mean something quite different if the 55 landed in 50 specs than if they landed in 6.

**What this does not settle.** The census itself. Whether an assignment would misfile a solution — the qualifier doing the real work in the threshold — cannot be judged from a directory listing, only from reading each spec. And nothing about desirability or viability; this is a feasibility measurement over committed code.

_Method: `ost_read_repo` listings of seventeen directories under `test/` in the OST-Agent repository, matched against every `instrument:` field in this vault, 2026-08-10. Read of committed code; no command executed, no result recorded, this node's rung unchanged._
