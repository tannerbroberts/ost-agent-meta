---
type: Assumption
source: 'agent-ideated:2026-08-19-unattended-sweep'
created: '2026-08-19'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Ask someone with the build loop's source and persisted state open whether a per-target failure record already exists across firings]]
[[A target whose instrument stayed red after a build is skipped by the next firing]]

Feasibility assumption. This solution only adds value if no such cross-firing memory already exists — settleable by reading the loop's own source and its persisted state directory, not by asking anyone what they want.

## Read from source rather than asked of a person (2026-08-22 unattended sweep, repo sight held)

The test beneath this assumption is an ask — "Ask someone with the build loop's source and persisted state open whether a per-target failure record already exists across firings" — and it has sat on the `outstandingAsks` queue unanswered. **The build loop's source and its persisted state are both in this repository, so this is a question a spec settles, not one that should cost a person an afternoon.** What follows is a first-party read, offered as input to whoever answers the ask rather than as the answer.

**Where the loop's own cross-firing state lives.** `src/loop/state.ts` establishes `.git/ost-agent/` as the loop's record directory, deliberately inside `.git` so that `git add -A` in every mutating MCP tool cannot sweep it into a commit. Its module docstring names exactly two files as the ones a firing must be able to write: **the health ledger and the firing lock.** Neither is per-target. `requireLoopStateDir` is fail-closed — a firing that cannot record does not happen — so the directory is a real, guaranteed-writable home for a ledger like the one this solution proposes; the mechanism has somewhere to live.

**What cross-firing memory does exist.** `src/loop/corrections.ts` is the one cross-session ledger this tree has previously recorded reading, and it records refused tool calls, dropping non-zero exits. That is a record of *how a call was composed wrongly*, not of *which build target failed its own instrument*. `src/loop/` holds no module named for build-target selection at all — the 28 files are lock, health, journal, spend, stall, scope, cadence, claim, replay and kin.

**So the assumption reads as probably true, and is not confirmed.** Nothing in the state directory's stated contract or in `src/loop/`'s file list holds a per-target attempt record. Two things this read does not settle, and they are why the ask still stands: the build loop's driver is `examples/automation/build-pass.sh`, which was not read in full this pass, and "no module named for it" is absence of evidence about a record that could be written by the driver script rather than by a `src/loop/` module.

_Method: first-party `ost_read_repo` of `src/loop/state.ts` in full (`"truncated": false`) and of the `src/loop/` listing. Nothing executed. Grounds feasibility only; silent on whether the re-selection bug is worth fixing this way. Rung stays at the `assertion` floor._
