---
type: AssumptionTest
source: 'agent-ideation:2026-08-21-unattended-sweep'
created: '2026-08-21'
evidence: assertion
threshold: >-
  All 2 assertions in test/tools/probe-script.test.ts pass: (1) package.json
  `scripts` has a `probe` entry whose command invokes `tsx -e` (or `tsx
  --eval`); (2) `npm run probe -- 'import { z } from "zod"; await
  import("./src/index.js"); console.log("probe-ok:" + typeof z.string)'` spawned
  with cwd at the repo root exits 0 and its stdout contains `probe-ok:function`.
instrument: npx vitest run test/tools/probe-script.test.ts
sight: grounded
---
#AssumptionTest #feasibility #build-loop #unvalidated #evidence/assertion

**Lane: compute-only.** A spec that spawns one npm script and reads its exit code settles it; nobody outside the building is the measurement.

**What the spec must assert, stated so the next reader does not inherit a blank file.**

1. Read `package.json` from the repo root; `expect(pkg.scripts.probe).toMatch(/tsx (-e|--eval)/)`. Today `scripts` holds `build`, `bundle`, `dev`, `gen:skill`, `test`, `test:watch` and no `probe` — read this pass via `ost_read_repo` — so this assertion fails on the current file for a reason specific to this test.
2. `execFileSync("npm", ["run", "probe", "--", "<the inline code in the threshold>"], { cwd: root, encoding: "utf8" })` does not throw and its output contains `probe-ok:function`. This is the assertion that carries the belief: it loads a bare dependency (`zod`, a declared dependency) and a repo-relative ESM path (`./src/index.js`, which exists as `src/index.ts`) from evaluated code, and fails if either resolves against anything but the repo root or if `tsx -e` refuses TypeScript/ESM input.

**Why it is red today, honestly classified.** The spec file does not exist, so today's red is `no-spec` — it would fail identically for any question written on this path and grants no build permit. It becomes a real red the moment the spec above is written: assertion (1) fails against the current `package.json`. A pass on this surface can name the mechanism but cannot leave the spec behind; the deliverable is the failing spec, not this filename.

**What a green does NOT settle.** Whether an agent reaches for `npm run probe` instead of a `/tmp` file when nobody is watching (behaviour across firings); whether a realistic probe survives shell quoting through `npm run -- '…'` (the spec uses one friendly line); and whether anyone wanted the turn back (desirability).
