---
type: Solution
source: 'agent-ideation:2026-08-21-unattended-sweep'
created: '2026-08-21'
evidence: assertion
---
#Solution #build-loop #unvalidated #evidence/assertion
[[Inline code handed to tsx from the repo root resolves bare packages and . src paths the same way a checked-in file does]]

**Variation dimension: automated-vs-manual — position: the resolution is automated; the probe's authorship stays manual.** `package.json` gains a `probe` script — `tsx -e` pinned to the repo root — so the agent runs `npm run probe -- 'import { x } from "./src/ost/thing.js"; console.log(await x())'` and the code is evaluated where bare packages and `./src` paths both resolve. There is no file, so there is no place for the file to be wrong. What is deliberately left manual is writing the probe itself: the script does not guess what the agent wants to see, it only guarantees that whatever the agent writes will load.

**Mechanism, grounded in the repo as read this pass.** `package.json` has `"type": "module"`, `tsx` as a devDependency, and a `dev` script that already runs `tsx src/cli/index.ts`; it has no `probe` script. Node resolves imports in evaluated code relative to the process cwd, and `npm run` sets cwd to the package root, so a `probe` script inherits the repo's resolution without any loader configuration.

**Compared to the siblings.** The scratch-directory candidate is cheaper and changes no `package.json`, but still produces a file that a habit can put in the wrong place; the vitest-probe candidate gives a harness this does not. This is the only one of the three that removes the failing artefact rather than relocating it — and it pays for that with a one-line ceiling: a probe that needs a loop, a fixture, or more than a few statements does not fit on a command line and pushes the agent back to a file.

**What it gives up.** Shell quoting. A probe containing both single and double quotes is painful to pass through `npm run -- '…'`, which is a new friction traded for the old one.

⚠️ Unvalidated. Agent-ideated from two transcript records; no operator has said the lost turn matters to them.
