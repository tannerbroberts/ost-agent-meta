---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  The manifests catch the known failure, and each omits at most 1 real
  dependency.
instrument: npx vitest run test/runner/helper-manifest-coverage.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that requirements can be declared accurately enough to catch real failures. A manifest covers only what someone remembered to declare, and a script that grows a new dependency after its manifest was written installs cleanly and fails at run time exactly as before.

**Risk category: feasibility.**

**Design.** Write manifests for every helper this project currently installs, by hand, without looking at the known failure. Then check each against the machine and see whether the `mapfile` failure — and any other latent incompatibility — is caught. Separately, diff each hand-written manifest against what the script actually uses, to measure how much a careful author misses.

**Why it is small.** A handful of helpers, one manifest each.

**What it will not cover.** Manifests written now, knowing this class of problem exists, are more careful than ones written routinely. The diff against actual usage is the honest measure and should be weighted above the catch.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/runner/helper-manifest-coverage.test.ts — The threshold — the manifests catch the known failure, and each omits at most 1 real dependency — is a diff between two things the repository holds: the spec loads each helper's declared manifest, extracts the commands and builtins the script actually invokes, asserts `mapfile` is declared, and asserts no manifest omits more than one command its script genuinely uses. It fails today because no helper carries a manifest.

## Instrument Log
- 2026-08-07 **red** (exit 1) `npx vitest run test/runner/helper-manifest-coverage.test.ts` — No test files found, exiting with code 1
- 2026-08-22 **green** (exit 0) `npx vitest run test/runner/helper-manifest-coverage.test.ts` — Duration  318ms (transform 35ms, setup 0ms, collect 72ms, tests 20ms, environment 0ms, prepare 38ms)
