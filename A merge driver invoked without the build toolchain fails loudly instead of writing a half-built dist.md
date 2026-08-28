---
type: AssumptionTest
source: 'TRANSCRIPT:0459d729-8ee3-43fc-ae1f-f05928ad84e2'
created: '2026-08-21'
evidence: assertion
threshold: >-
  All 3 toolchain-absent cases (esbuild missing, node_modules missing, bundle
  script exiting non-zero) leave the conflict unresolved and exit non-zero; 0 of
  the 3 may produce a dist file, and the 1 toolchain-present case must resolve
  by rebuilding.
instrument: npx vitest run test/git/dist-merge-driver-toolchain.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption above is a feasibility belief about the environment: that whatever process resolves the merge can actually run the project's build when the driver invokes it. This test does not try to survey every environment — it makes the assumption safe to be wrong about, which is cheaper and is the thing that actually protects a firing.

**Why the environment survey is the wrong test to write.** The parent assumption's own wording concedes the merge may run in "a lighter-weight or more sandboxed context than a full firing". Enumerating those contexts is open-ended and ages badly. What matters is the failure mode: if the driver runs the build and the toolchain is absent, does the firing get a loud refusal, or does it get a `dist/ost-agent.mjs` that is truncated, empty, or stale — committed, and read as authoritative by everything downstream?

**What the repository already says, and why it makes this the live risk rather than a hypothetical.** `examples/automation/build-pass.sh` invokes `node "$OST_AGENT_DIR/dist/ost-agent.mjs"` for `build-check`, `gate`, `buildable`, `verify`, `check` and `debt`, and contains no `npm ci` and no `npm run bundle` anywhere. So the committed automation assumes a prebuilt bundle is present and never guarantees the toolchain that produces one is installed. A merge driver is the first thing on that path that would need `esbuild` at merge time, and nothing upstream of it establishes that `esbuild` is there.

**Pre-committed bar, fixed before anything runs.** Four cases, three of them absence cases. With `esbuild` unavailable, with `node_modules` absent, and with the `bundle` script exiting non-zero, the driver must in each case exit non-zero and leave the conflict unresolved — zero of the three may leave a `dist/ost-agent.mjs` behind, because a partial artifact is worse than an unresolved conflict: the conflict stops the firing where a bad bundle silently poisons the next six CLI calls. With the toolchain present, the fourth case must resolve the conflict by rebuilding from the merged source.

**What a green here does not settle.** It says nothing about whether the build is deterministic — that is the sibling test beneath this same solution — and nothing about how often the toolchain is actually absent in the operator's real firings, which stays an environment question. It also says nothing about desirability or viability: a driver that refuses safely is still a driver nobody has asked for.

**Instrument honesty, stated rather than hidden.** This is a `no-spec` red: `test/git/dist-merge-driver-toolchain.test.ts` does not exist, so the command fails today for the weakest available reason. That is not a choice — `ost_set_instrument` accepts only a bare `npx vitest run <path>.test.ts` and refuses any test-name filter, so an assertion-specific red inside an existing spec cannot be expressed on this surface at all (measured this pass; recorded on "My instruments are red because a file is absent, not because the behaviour is"). Two things are done to make it as strong as the grammar allows: the path sits in `test/git/`, a directory that exists and holds six sibling specs, so the builder inherits the neighbourhood's conventions rather than a structural decision; and the threshold above names the four cases and the bar, which is what this tree's one observed weak-red lifecycle showed a builder actually works from.

⚠️ Proposed only — the agent does not run tests or record results.

## Instrument Log
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-24 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-24 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-25 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-26 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-26 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-26 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-27 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-27 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-27 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-27 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-27 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-27 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-28 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-28 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-28 **no-spec** (exit none) `npx vitest run test/git/dist-merge-driver-toolchain.test.ts` — test/git/dist-merge-driver-toolchain.test.ts does not exist — no spec was collected, so nothing was measured
