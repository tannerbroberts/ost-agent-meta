---
type: Solution
source: 'agent-ideation:2026-08-21-unattended-sweep'
created: '2026-08-21'
evidence: assertion
---
#Solution #build-loop #unvalidated #evidence/assertion
[[A probe spec can be kept out of the default vitest run and still run when named, using the argv check the config already applies to contended files]]

**Variation dimension: bought-vs-built — position: adopt vitest as-is as the probe runner; build nothing but a config line, a gitignore line and a prompt sentence.** A probe is written as `test/<area>/<anything>.probe.test.ts` and run with `npx vitest run test/<area>/<anything>.probe.test.ts`. The file sits inside the repo, so imports resolve; vitest supplies `expect`, fixtures, the same `root` resolution every committed spec uses, and the familiar red/green output. Nothing new is authored in this repository: the runner, the harness and the resolution are all already bought.

**Mechanism, grounded in the repo as read this pass.** `vitest.config.ts` has `include: ["test/**/*.test.ts"]` and already carries a `CONTENDED` list of files that "run only when named on the command line", implemented with a `namedOnCommandLine()` argv check — and its own comment explains why that check exists: "vitest applies `exclude` before CLI filters, so an excluded file cannot be reached by naming it." A `**/*.probe.test.ts` glob goes into the same mechanism, so a probe left behind cannot turn `npx vitest run` red, and `.gitignore` gains `*.probe.test.ts` so it cannot ship.

**Compared to the siblings.** The scratch-directory candidate needs no config change but gives the probe no harness; the inline-eval script removes the file but caps a probe at one line. This is the only candidate under which a probe that turns out to be worth keeping is already a spec — rename it and commit it — which is the path `CLAUDE.md` asks for ("prefer converting a finding into a committed test over recording it as prose").

**What it gives up.** A probe is not a test, and dressing it as one invites the file to be committed as if it were. The argv-exclusion trick is the config's own workaround for a vitest limitation and is the part most likely to break on a vitest upgrade.

⚠️ Unvalidated. Agent-ideated from two transcript records; no operator has said the lost turn matters to them.

## Definition of done

"A probe spec is absent from the bare vitest run, present when named, and gitignored"

```
npx vitest run test/config/probe-spec-by-name-only.test.ts
```

Red today as `no-spec` — the file is not written. The test node names the three assertions it must hold (`vitest.config.ts` routes `**/*.probe.test.ts` through the existing `namedOnCommandLine` gate; a fixture probe is absent from a bare `npx vitest run` and present when named, checked by spawning the runner twice with `--reporter=json`; `.gitignore` lists `*.probe.test.ts`), the first and third of which fail against today's config and `.gitignore`. The second is the one that can refute the assumption outright — the config's own comment says `exclude` beats CLI filters — and is the reason this candidate is worth a spec rather than a sentence. A green proves the runner mechanics; it says nothing about whether a probe dressed as a spec ends up committed as one, or whether anyone wanted the turn back.
