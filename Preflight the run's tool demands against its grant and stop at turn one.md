---
type: Solution
status: unvalidated
source: 'TRANSCRIPT:8a9777ad-a1ca-47fc-ab8e-3bd4b001a5cd'
created: '2026-08-06'
evidence: observed
---
#Solution #unvalidated #evidence/observed
[[A session can find out which tools it may call without calling one]]

Before the run reads the tree, it works out what it is going to need and whether it has it.

The instructions an unattended pass fires with already name their tools — the skill declares `allowed-tools` in frontmatter, and the prompt names `ost_check`, `ost_debt`, `ost_flag_humans_required` in prose. The session, separately, holds a grant. Nothing today compares the two. The run finds the gap by falling into it, four denials deep, at the point where it had already decided what it wanted to do.

The proposal is one comparison at the top of the pass: enumerate the tool names the instructions demand, enumerate what this session can actually call, and if the second does not cover the first, exit before touching the vault with a message naming exactly the missing grants and the settings file they go in.

The bet is that failing loudly at turn one is cheaper than failing quietly at turn forty. A run that stops with "I need these four grants" costs the operator one morning of reading and one edit. A run that proceeds costs a night of compute and produces a report indistinguishable from a night where there was nothing to do.

What this deliberately does not do is guess. It does not request the grant, escalate, or work around the gap — the whole point of a permission is that a person decides, and a preflight that helpfully acquires what it lacks has voided the mechanism it was meant to serve.

Contrast with its siblings: "The run's report leads with what it was refused, so a denied night cannot read as a quiet one" accepts the gap and fixes the reporting instead; "Derive the permission allowlist from the skill's own allowed-tools, so the two lists cannot drift" removes the gap by construction and would make this preflight redundant. This one is the cheapest to build and the only one of the three that helps when the mismatch is the operator's deliberate choice rather than a drift.

The cost is a false stop: a pass that could have done nine tenths of its work refuses to do any of it because one optional tool is missing. That is the risk worth testing before building.

## Definition of done

"Resolve the declared tool list against the settings allowlist and name every gap, including path-scoped ones"

```
npx vitest run test/runner/grant-preflight.test.ts
```

Red today: `test/runner/grant-preflight.test.ts` does not exist, and neither does the resolver it would exercise. A builder should treat the spec's assertions as the specification — four omitted grants named, the path-scoped read gap named, zero false gaps against a pattern-granted entry — and not merely as a file that needs to exist.

Green here proves feasibility and nothing else. Whether stopping the entire pass over one missing optional tool is what an operator wants is untested and needs a person.
