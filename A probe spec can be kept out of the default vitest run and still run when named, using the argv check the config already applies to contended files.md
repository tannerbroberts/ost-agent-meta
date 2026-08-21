---
type: Assumption
source: 'agent-ideation:2026-08-21-unattended-sweep'
created: '2026-08-21'
evidence: assertion
---
#Assumption #feasibility #build-loop #unvalidated #evidence/assertion
[[A probe spec is absent from the bare vitest run, present when named, and gitignored]]

**The belief (feasibility).** Adding a `**/*.probe.test.ts` glob to `vitest.config.ts`'s `exclude` — gated by the same `namedOnCommandLine()` check the `CONTENDED` list already uses — makes a probe invisible to `npx vitest run` and reachable by `npx vitest run test/<area>/<name>.probe.test.ts`, and `.gitignore` listing `*.probe.test.ts` keeps it out of every commit.

**How it could be false.** `namedOnCommandLine()` matches on the file's stem via `arg.includes(stem)`, which was written for one literal filename and may not generalise to a glob — a glob has no single stem, so the exclusion may be all-or-nothing; vitest's include/exclude evaluation order may differ for globs versus literal paths; or a future vitest may apply CLI filters before `exclude` and silently make the gate unnecessary (harmless) or invert it (harmful). The config's own comment records that the order is a vitest behaviour, not this repo's choice.

**Why this is a repository question.** A spec that spawns `npx vitest run` twice — once bare, once naming a fixture probe — and compares which files each run reports settles it mechanically. What it cannot settle is whether a probe dressed as a spec tempts the agent to commit it as one; that is a habit, observed over firings.

⚠️ Unvalidated. Agent-ideated.
