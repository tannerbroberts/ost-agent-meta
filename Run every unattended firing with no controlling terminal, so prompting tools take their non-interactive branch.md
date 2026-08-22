---
type: Solution
status: unvalidated
source: 'agent-ideated:2026-08-22-unattended-sweep'
created: '2026-08-22'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Without a controlling terminal the prompting tool fails loudly instead of silently taking its default]]

**Variation dimension: who-does-the-work — nobody does, because the step is removed.** The other candidates decide who answers the prompt. This one arranges for the prompt never to be asked. A firing is launched with stdin closed and no controlling terminal, and with the environment variables the common offenders read (`CI`, `DEBIAN_FRONTEND=noninteractive`, `GIT_TERMINAL_PROMPT=0`). Well-behaved tools detect the absent TTY and take the branch they already have for pipelines and CI; the one that prompted in the founding evidence would have overwritten or refused loudly instead of defaulting to no in silence.

**Why this shape.** It is the only candidate that does not need to enumerate anything. A policy file has to name the prompts it may answer, and a flag lint has to know each tool's flag; both are lists that go stale the moment a new tool enters the automation. Absence of a TTY is a property of the launch, so it covers every tool that was ever going to prompt, including ones nobody has added yet.

**What it gives up, stated so it can be judged against the siblings.** It removes the question without deciding the answer — a tool whose non-interactive default is "no" still declines, it just declines legibly instead of silently. So this candidate converts a silent wrong outcome into a loud failure, which is strictly better and is not the same as getting the work done. It also depends on tools being well-behaved: one that reads `/dev/tty` directly rather than checking `isatty` will hang instead of failing, which is a worse outcome than today's.

**Cost.** A change to how `examples/automation/autonomous-pass.sh` and `build-pass.sh` invoke the session, plus the environment block. No new module.

⚠️ Unvalidated. Agent-ideated from one recorded session (`005ca37f`, `overwrite src/cli/index.ts? (y/n [n]) not overwritten`).

## Definition of done

"A prompting command run with no controlling terminal exits non-zero with its question on stderr, and does not silently default"

```
npx vitest run test/automation/no-tty-prompt-behaviour.test.ts
```

Red today as a no-spec filing, with a bound bar so it is a working permit rather than a vacuous red. The spec settles feasibility — does removing the TTY make the failure legible — and nothing else. Whether a loud refusal is an acceptable outcome, given that the work still does not get done, is a person's call and belongs with the sibling candidates.
