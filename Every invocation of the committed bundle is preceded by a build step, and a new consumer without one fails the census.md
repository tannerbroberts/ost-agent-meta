---
type: AssumptionTest
source: 'TRANSCRIPT:0459d729-8ee3-43fc-ae1f-f05928ad84e2'
created: '2026-08-21'
evidence: assertion
threshold: >-
  The census finds every path invoking dist/ost-agent.mjs and requires a build
  step earlier in the same script or job: 0 consumers may invoke it unbuilt, and
  a planted 4th consumer with no build step must be reported by name rather than
  passing silently.
instrument: npx vitest run test/release/dist-consumer-inventory.test.ts
sight: grounded
---
#AssumptionTest #unvalidated #evidence/assertion

This solution untracks the compiled bundle and has every firing build it. Whether that is possible turns on one enumerable fact — who runs `dist/ost-agent.mjs` today, and would each of them still work if the file were not in the checkout. The Issues note on the parent solution deferred this for want of repo sight; this pass had it, so what follows is a partial inventory read off committed code, and the test is written to finish and then defend it.

**Two consumers confirmed, and both would break as written.**

- `examples/automation/build-pass.sh` sets `CLI="$OST_AGENT_DIR/dist/ost-agent.mjs"` and invokes `node "$CLI"` for six calls per firing — `build-check`, `gate`, `buildable`, `verify`, `check`, `debt`. It contains no `npm ci`, no `npm install` and no `npm run bundle`.
- `examples/automation/github-workflow.yml` checks OST-Agent out with `actions/checkout@v4` into `.ost-agent-src` and writes an MCP config pointing at `node "$SRC/dist/ost-agent.mjs" mcp`. The job installs Node and `@anthropic-ai/claude-code` and never installs this project's dependencies or runs its build. This one is the sharper case: it runs on a fresh runner, so it depends on the bundle arriving from git and on nothing else.

**Not confirmed, and named so nobody mistakes this for a complete list.** `examples/automation/autonomous-pass.sh` is 20KB and could not be read whole on this surface; whether it invokes the bundle is unchecked. Any published-package or plugin-host consumer is also unchecked. Completing the inventory is the first thing the spec does, and is why this is a census rather than two assertions.

**Why the assumption survives this read rather than being refuted by it.** Both confirmed consumers *can* be changed — a `npm ci && npm run bundle` step in the workflow job and in the build loop's preflight is a small edit. What the read establishes is the cost the parent solution's body called "may be a larger change than it looks": it is a build step on the critical path of every scheduled CI run and every hourly firing, on a runner that currently installs nothing from this project. That is a real per-firing tax, and it is the thing to weigh against the merge-driver sibling, which keeps the bundle committed and pays only on conflict.

**Pre-committed bar, fixed before anything runs.** The census walks the repository for every invocation of `dist/ost-agent.mjs` and requires a build step earlier in the same script or job. Zero consumers may invoke it unbuilt. Non-vacuity is asserted in the same spec, in the manner `test/loop/firing-residue.test.ts` already uses for `FIRING_RESIDUE_PREFIXES`: plant a fourth consumer with no build step and require the census to name it, so a census that has quietly stopped matching anything cannot pass.

**What a green here does not settle.** Nothing about whether untracking is the right call — a complete inventory with every consumer converted still leaves the per-firing build cost, which is a viability judgement and nobody's to make mechanically. It also says nothing about consumers outside this repository: an install path, a plugin host, or a second machine loading the bundle would be invisible to a census that walks only these files, and that residue is exactly what the sibling questions to the operator are for.

**Instrument honesty, stated rather than hidden.** This is a `no-spec` red: `test/release/dist-consumer-inventory.test.ts` does not exist, so the command fails today for the weakest available reason. Forced rather than chosen — `ost_set_instrument` accepts only a bare `npx vitest run <path>.test.ts` and refuses any test-name filter, so an assertion-specific red inside an existing spec is not expressible on this surface (measured this pass; recorded on "My instruments are red because a file is absent, not because the behaviour is"). The path sits in `test/release/`, a directory that exists, and the planted-consumer technique is copied from a spec already committed, so the builder inherits both a neighbourhood and a pattern rather than a structural decision.

⚠️ Proposed only — the agent does not run tests or record results.
