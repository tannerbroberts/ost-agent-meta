---
type: Solution
source: 'TRANSCRIPT:9a406570-323c-453a-b4ca-a29b4aa01f18'
created: '2026-08-05'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[The failures this would prevent happened in directories this tool actually created]]

Whatever creates a workspace leaves a small machine-readable record of what it set up and, more importantly, what it deliberately did not: `git: false`, `deps-installed: false`, `remote: none`. Any later reader gets the state by reading one file instead of probing for it.

**The writer pays, once, and every reader benefits.** That is the axis this sits on against "One workspace-state probe the run makes before it plans, not one failing command at a time", where each reader pays every time, and against "Scaffolding initialises unconditionally, so the state is never in question", where nobody pays because there is nothing to record.

**Why this shape is tempting here specifically.** In every captured instance the folder had just been scaffolded, minutes earlier, by a process that knew perfectly well it had not run `git init`. The information existed and was thrown away. Recovering it later by probing is paying to reconstruct something that was free at the moment of creation.

**And why that argument is weaker than it sounds.** It holds only for workspaces this tool scaffolded. A folder a person made, or another tool made, or that was cloned, has no manifest — and a reader that trusts manifests has to handle their absence anyway, which is the probe. So this may be an optimisation on top of a probe rather than an alternative to one, and a fair comparison should ask whether it earns its own existence once the fallback is built.

**The failure mode to test for.** A manifest is a claim about state, not the state itself, and claims go stale — somebody runs `git init` by hand and the file now lies. A stale manifest is worse than no manifest, because a probe that finds nothing degrades to asking, while a reader that believes a wrong manifest proceeds confidently. Any version of this needs an answer for staleness before it is worth building.

_Agent-ideated, unvalidated — one of three competing candidates under this opportunity, for a human to compare rather than adopt._

## Definition of done

"Count how many captured failures happened in a directory this tool actually scaffolded"

```
npx vitest run test/runner/scaffold-manifest-coverage.test.ts
```

Red today: nothing in the repository records what a scaffolder initialised, so there is no manifest to check coverage against. Green when at least three of the four captured exit-128 failures are shown to have occurred in tool-created directories.

**What this does not settle.** Staleness, which is this candidate's real hazard — a manifest is a claim about state, not the state, and a reader that believes a wrong one proceeds confidently where a probe that finds nothing degrades to asking. Nothing in four captured sessions can show that; it needs a period of real use.

## History
- 2026-08-05 unlinked "Count how many captured failures happened in a directory this tool actually scaffolded" — moved under "The failures this would prevent happened in directories this tool actually created" — the belief this test measures now has a node of its own
