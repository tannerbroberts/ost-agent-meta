---
type: AssumptionTest
created: '2026-08-22'
evidence: assertion
threshold: >-
  zero automation entrypoints invoke dist/ without a preceding build step, and
  the offered and read counts are equal and greater than one
instrument: npx vitest run test/automation/dist-consumers-build-first.test.ts
sight: grounded
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.** Nobody is the measurement: this reads committed files and counts, and the answer does not depend on anyone's preference.

**Design.** Enumerate every entrypoint under `examples/automation/` (and any other committed script or workflow that references `dist/`). For each, assert that a build step precedes the first invocation of the bundle, or that the file explicitly declares a stale bundle acceptable. Report the denominator — entrypoints offered and entrypoints read — so a scan whose subject moved comes out blind rather than clean, the rule `src/ost/sweep.ts` already sets for sweeps in this repo.

**Pre-committed threshold:** zero entrypoints invoke `dist/` without a preceding build step or an explicit stale-is-fine declaration, and the offered and read counts are equal and greater than one.

**Why it is red today, specifically.** `examples/automation/build-pass.sh` was read in full this pass: it assigns `CLI="$OST_AGENT_DIR/dist/ost-agent.mjs"` and reaches `node "$CLI" build-check` with no build anywhere above it. That is one entrypoint failing the bar, so the assertion fails on a named file rather than on the spec's absence — the spec file itself is also unwritten, so the first observation will file `no-spec`, but the bar above is fixed and the failing case is already identified by name.

**What this does not settle.** Whether the consumers *need* a current bundle at all — a stale one may serve them, and that is the sibling assumption and the operator's call. A green here means the dependency on trunk dist has been removed, not that removing it was the right trade against a custom merge driver or a fresh worktree per firing.
