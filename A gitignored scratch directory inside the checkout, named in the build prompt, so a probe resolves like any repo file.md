---
type: Solution
source: 'agent-ideation:2026-08-21-unattended-sweep'
created: '2026-08-21'
evidence: assertion
---
#Solution #build-loop #unvalidated #evidence/assertion
[[The build prompt and gitignore alone can put probes inside the checkout, where they resolve the repo's modules and never reach a commit]]

**Variation dimension: who-does-the-work — position: nobody, because the step is removed.** No person writes tooling and no agent learns a new command. The repository gains one gitignored directory (say `.scratch/`), and `examples/automation/build-pass.sh`'s prompt says in one sentence that throwaway probes go there and nowhere else. A file under the checkout resolves `@modelcontextprotocol/sdk` from the repo's `node_modules` and `./src/...` from the repo root by Node's ordinary rules — the resolution question the two observed sessions paid a turn for never arises, so nobody answers it.

**Mechanism.** `.gitignore` already excludes `.superpowers/` as "SDD scratch" — the pattern exists; this adds a sibling entry for probes. `build-pass.sh` already tells the model where its report goes; the same prompt names the probe directory. `npx tsx .scratch/whatever.ts` then runs with the repo's loader and dependencies.

**Compared to the siblings.** The inline-eval `probe` script beside it removes the file entirely but asks the agent to learn a new command and fit a probe on one line; the vitest-probe candidate gives the probe a test harness at the price of vitest's include/exclude semantics. This one is the least to build and the least to remember, and it is also the weakest guarantee: it relies on the session reading and following one sentence of prompt, and a session that reaches for `/tmp` out of habit is exactly as broken as today.

**What it gives up.** Nothing enforces it. A probe left in `.scratch/` is invisible to git and therefore to review, which is the point for throwaway code and a liability the moment a probe grows into something worth keeping.

⚠️ Unvalidated. Agent-ideated from two transcript records; no operator has said the lost turn matters to them.

## Definition of done

"The build prompt names the in-checkout probe directory, gitignore excludes it, and a probe under it loads the repo's modules"

```
npx vitest run test/automation/build-pass-probe-location.test.ts
```

Red today as `no-spec` — the file is not written. The test node names the three assertions it must hold (the prompt heredoc names `.scratch/` and warns off `/tmp`; `.gitignore` lists `.scratch/`; a fixture under `.scratch/` importing `@modelcontextprotocol/sdk` and `../src/index.js` runs green under `npx tsx`), the first two of which fail against today's `examples/automation/build-pass.sh` and `.gitignore`. A green proves the location is named and resolves; it says nothing about whether a session follows the instruction or whether anyone wanted the turn back.
