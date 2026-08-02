---
type: Solution
created: '2026-07-27'
evidence: assertion
---
#Solution #evidence/assertion
[[Try to reproduce ten recorded failures from the record alone]]

**The idea.** `loop step` records `cwd` and the resolved argv next to the exit code it already stores, so a recorded failure can be re-run verbatim from the record.

**What produced it.** Observed twice in one pass (2026-07-27): the same command recorded exit 1 and exit 0 in the same run, differing only in the directory it was invoked from, with nothing in the record naming that difference. The health file is deterministic, append-only, and — for those two entries — not diagnostic.

**Why it is worth more than it looks.** The whole health-bookend design rests on a claim that the record is the thing you can trust when nobody was watching. A number that cannot be reproduced from its own record weakens that claim in exactly the place the design is load-bearing. This is one field.

**Where it fails.** `cwd` is necessary and not sufficient — environment variables, the node/pnpm version, and the state of `node_modules` all move the exit code too, and recording all of them turns a health record into a container image. There is a real judgement about where to stop, and this node does not answer it; it argues only that the directory is on the necessary side of any reasonable line.

⚠️ Unvalidated. Agent-ideated from an observed failure in this pass's own health record.

## Shipped 2026-07-27 in v0.20.0 — and the gap was wider than the node said

`LoopStepRecord` now carries optional `cwd` and `argv`. `cwd` is captured **before** the
child spawns — reading it afterwards would report wherever the process ended up rather than
where the command was given.

**Both halves showed up live in the firing that shipped it**, which is why the second half
exists at all. The node named the missing `cwd`. It did not name the second defect: `command`
is an `argv.join(" ")`, so a single argument containing a space records identically to two
arguments, and no reader can tell them apart. Both are now recorded.

The observed failure: `ost-agent loop step --phase build -- pnpm --filter @tetrix/backend test`
invoked from the vault directory rather than the repo produced **no output at all** and
recorded a line indistinguishable from the same command run correctly. Re-running it from the
repo worked. Without `cwd`, nothing in the record could have told those two lines apart.

Both fields are **optional**, because `runs.jsonl` is append-only: every line written before
this release lacks them, and a reader that threw on older lines would go blind at exactly the
moment the history matters.

## History
- 2026-08-01 evidence: observed → assertion — demoted by the fifteenth pass — B3's rung-unearned guard (v0.23.0-line) shipped after this node was authored; its source is not a TRANSCRIPT: recording, so 'observed' was unearned. Demotion only, per rungs.ts's own remedy.
