---
type: Opportunity
status: unvalidated
source: 'TRANSCRIPT:f48dc76d-9bb6-45c3-b624-5b386609d720'
created: '2026-08-02'
evidence: observed
---
#Opportunity #unvalidated #evidence/observed
[[The pass ends at the handoff, and the finished check wakes the next one]]
[[One cheap blocking wait replaces the poll-and-retry loop]]
[[Take up independent work while a check is outstanding]]

One captured session's entire friction record is a command that timed out after two minutes, having reported `still pending` five times in a row. Across the week the same shape recurs in at least eleven sessions: check the pull request, find it pending, wait, check again. Some of those attempts exit 143 on a timeout; the rest are refused outright for pairing a sleep with the check.

The verification the loop depends on is asynchronous and the only way it can be observed is by asking repeatedly. So the agent polls, and polling is both the natural instinct and the thing the environment declines to make cheap. Time that reads as work in the record is time spent waiting, and a run's cost is dominated by an event it has no way to be notified of.

**The need:** I want to be told when the check finishes, rather than pay to keep asking whether it has.

More than one way to address this: subscribe to completion instead of polling for it, hand the wait to something built to block cheaply, structure the pass so that other work proceeds while a check is outstanding, or end the pass at the handoff and resume when the result lands.

## Provenance

Distilled from `TRANSCRIPT:f48dc76d-9bb6-45c3-b624-5b386609d720`, whose only friction event is a two-minute timeout after five pending attempts.

Corroborated across `0d27cebf`, `470cb94a`, `4ff7b605`, `516fdfb8`, `5960b7ec`, `5bbed804`, `87a025f8`, `97546e2f`, `995b8ab1`, `a0eb3fd4`, `a615eb46`, `b7aae32d` and `e335a680` — every one of them polling a pull request's checks.

## Sharper measurement — unattended sweep, 2026-08-02 (sixth pass)

This node's body says the shape recurs "in at least eleven sessions." Re-reading the twenty-two transcript records outstanding this pass gives a tighter and more damning count, so it is recorded here rather than left as an estimate.

**Twelve of the twenty-two sessions contain a blocked sleep-then-check.** Eleven of them are specifically `sleep N` followed by `gh pr checks <N>`, and the pull request numbers are `9`, `10`, `12`, `13`, `14`, `17`, `18`, `19`, `22`, `25` and `30`. That is the point worth having: this is not eleven repetitions against one stubborn check, it is **eleven distinct pull requests**, spread across the numbering from #9 to #30, each one polled with the identical construct and refused with the identical message. The sleep interval varies (25, 30, 45, 60, 240 seconds) — the agent tunes the wait each time, which is evidence it is reasoning about the delay rather than pattern-matching a snippet, and still reaches for the one form the environment declines.

Two further instances are the same instinct pointed elsewhere: `0d27cebf` also blocked on `sleep 25` before tailing a log file, and `470cb94a` on `sleep 240` before a git status. So the need is not about pull requests. It is about any asynchronous completion the loop can only learn about by asking again.

The costed version, from the same records: `0d27cebf` carries a `Exit code 143 Command timed out after 2m 0s`, and `516fdfb8` and `5960b7ec` each carry `TaskOutput` retries with `block: true, timeout: 600000` — a ten-minute blocking wait, which is the same wait relocated to a tool that is permitted to hold it.

_Provenance: sessions `0d27cebf`, `470cb94a`, `4ff7b605`, `516fdfb8`, `5960b7ec`, `87a025f8`, `97546e2f`, `995b8ab1`, `a0eb3fd4`, `a615eb46`, `b7aae32d`, `e335a680`. Appended as corroboration; the mapped ledger is unchanged, per the standing disposition rule recorded on the root._

## Corroboration — twelve sessions, eleven distinct PRs (unattended sweep, 2026-08-03)

This node was created from a single session. Twenty-two mechanically-captured sessions were read in full this pass, and **twelve of them contain this exact event**: the agent composed `sleep N && gh pr checks <PR>`, and the harness refused it with *"To wait for a condition, use Monitor with an until-loop … To wait for a command you started, use run_in_background"*.

The sessions are `0d27cebf`, `470cb94a`, `4ff7b605`, `516fdfb8`, `5960b7ec`, `87a025f8`, `97546e2f`, `995b8ab1`, `a0eb3fd4`, `a615eb46`, `b7aae32d`, and `e335a680`. The PR numbers named across them are 9, 10, 12, 13, 14, 17, 18, 19, 22, 25 and 30 — **eleven distinct pull requests**. Two sessions did it twice; `0d27cebf` slept against a log tail and then against `gh pr checks 30`, and `470cb94a` slept 240 seconds against `git status` before sleeping 45 against `gh pr checks 13`.

Three things make this stronger than a repeat count:

1. **It is not confined to CI.** The blocked waits also targeted `tail` on a log file, `ls` on a workflow journal directory, and `git status --porcelain` — the same shape wherever the loop needs to know when something outside it finished.
2. **The sanctioned path is also unsatisfying.** Session `516fdfb8` shows what happens when the agent does poll: `gh pr checks 17` exited 8 with `bundle-drift pass 14s` and `test pending 0` — a non-zero exit that means *not finished yet*, indistinguishable at the call site from a failure. The same session recorded three `TaskOutput` retries, each with `"block":true,"timeout":600000` — ten-minute blocking waits, re-issued.
3. **The agent keeps reaching for `sleep` anyway.** Across eight days and eleven PRs it never internalised the refusal, which is the same shape as [[The same refusal is rediscovered every session, because nothing carries the lesson forward]].

Sessions `fd2c6d71` (a bare `CronList` retry, its only friction event) and `92cc492d` point the same way.

_Source: the twelve `TRANSCRIPT:` records named above, each read in full this pass — observed behavior, captured mechanically from the agent's own transcripts. Grounds usability, not demand. Recorded as corroboration only; the node's rung is unchanged and promotion remains a human's call._

## Corroboration — a hand-rolled poll, refused as one command (unattended sweep, 2026-08-03)

`TRANSCRIPT:3d729ebc-348f-4d45-8f3c-25df1de8fbc9` records the wait in its most literal form: a Bash call of `sleep 45` followed by `gh run list --branch build-loop-and-reports --limit 5` and `gh pr view 33 --json mergeable,mergeStateStatus,statusCheckRollup`. A timer, a list, and a status read, stitched into one command because there is nothing to subscribe to — the session had to build its own polling loop out of `sleep`.

It did not even get to wait: the call was blocked before it ran. So the session paid twice — once for having no subscription, and once for the workaround that absence forced it into.

_Source: `TRANSCRIPT:3d729ebc-348f-4d45-8f3c-25df1de8fbc9`, read in full this pass — observed behavior from the agent's own transcript. Grounds usability, not demand. Corroboration only; the node's rung is unchanged._

## Corroborating sessions (2026-07-29 → 2026-08-04)

Nine separately-captured sessions show the same move: the run reaches for `sleep N && <poll>` to wait on a CI check or a background task, and the harness refuses it every time with the same message ("To wait for a condition, use Monitor with an until-loop").

- `TRANSCRIPT:785ea509-96b9-4225-b45a-babd5321aafc` — blocked on `sleep 25; gh pr checks 39`, then four near-identical full-suite re-runs while waiting.
- `TRANSCRIPT:516fdfb8-bab1-41a4-b1e5-92fde97bd90d` — blocked on `sleep 45; gh pr checks 17`; three `TaskOutput` block-polls of the same task id.
- `TRANSCRIPT:470cb94a-d709-43b1-85aa-dedd917ac866` — blocked on `sleep 240; …` waiting for a workflow journal to appear.
- `TRANSCRIPT:4ff7b605-da1d-4f2e-8c05-ec6408118837` — blocked on `sleep 45; ls …/workflows/wf_a51c57d4-bc9/`.
- `TRANSCRIPT:b7aae32d-150a-462f-9027-cdf7af12badd` — blocked on `sleep 45; gh pr checks 12`.
- `TRANSCRIPT:995b8ab1-5e55-4a5c-b05d-aaed9e1d7538` — blocked on `sleep 45; gh pr checks 9`.
- `TRANSCRIPT:e335a680-ee48-4171-b8ad-4cfb526e4129` — blocked on `sleep 45; gh pr checks 19`.
- `TRANSCRIPT:97546e2f-307a-46c7-a40e-64de3ec75f68` — blocked on `sleep 45; gh pr checks 18`.
- `TRANSCRIPT:a0eb3fd4-5a36-44c1-93fc-ac8b48258cff` — blocked on `sleep 25; gh pr checks 10`.

Two things the count says that the single-session record did not. First, the refusal message names the correct alternative and the run still reached for `sleep` in the next session — so this is not an instruction-reading failure that better docs would fix; the wait is a shape the run keeps wanting and cannot express. Second, the wait is not only CI: a workflow journal file and a background task id are waited on the same way, so a fix scoped to `gh pr checks` would leave most of the instances standing.

Evidence class is observed behaviour of this agent using its own harness — it grounds usability, not that anyone outside wants a fix.

## Corroboration — eight sessions, machine-recorded

Eight separate sessions in the transcript channel each contain the same refused call: a `sleep N` composed with `gh pr checks <n>`, blocked by the harness with the message that a condition should be waited on with an until-loop instead. The agent reached for the same unavailable primitive every time and learned it from the refusal every time.

| Evidence | Date | The blocked wait |
| --- | --- | --- |
| `TRANSCRIPT:8fc8d6e3-7cae-41e0-a83b-e32346e352b1` — see below, glob case | 2026-07-24 | — |
| `TRANSCRIPT:995b8ab1-5e55-4a5c-b05d-aaed9e1d7538` | 2026-07-29 | `sleep 45` → `gh pr checks 9` |
| `TRANSCRIPT:a0eb3fd4-5a36-44c1-93fc-ac8b48258cff` | 2026-07-29 | `sleep 25` → `gh pr checks 10` |
| `TRANSCRIPT:4ff7b605-da1d-4f2e-8c05-ec6408118837` | 2026-07-29 | `sleep 45` → `ls .../workflows/wf_a51c57d4-bc9/` |
| `TRANSCRIPT:470cb94a-d709-43b1-85aa-dedd917ac866` | 2026-07-30 | `sleep 240` → `git status`, then `sleep 45` → `gh pr checks 13` |
| `TRANSCRIPT:516fdfb8-bab1-41a4-b1e5-92fde97bd90d` | 2026-07-30 | `sleep 45` → `gh pr checks 17` |
| `TRANSCRIPT:97546e2f-307a-46c7-a40e-64de3ec75f68` | 2026-07-30 | `sleep 45` → `gh pr checks 18` |
| `TRANSCRIPT:87a025f8-c6b0-474f-9a13-0b5ec5c922ea` | 2026-07-31 | `sleep 30` → `gh pr checks 25` |
| `TRANSCRIPT:785ea509-96b9-4225-b45a-babd5321aafc` | 2026-08-04 | `sleep 25` → `gh pr checks 39` |

Two things this adds that the node did not already say:

1. **The wait is nearly always for CI on a pull request.** Seven of the nine blocked waits name `gh pr checks`. The unsubscribable check is not a general class — it is one check, on one service, and the loop has no way to be told when it finishes.
2. **The polling substitute costs its own turns.** In `516fdfb8` the same `npx tsc --noEmit && npx vitest run …` line is re-issued three times in one session, and `TaskOutput` is re-polled three times with byte-identical arguments; `785ea509` re-issues its suite command four times. Waiting is not free even after the refusal is understood — it converts into repeated polling.

One further datum on cost: in `785ea509` the agent then tried `Monitor` — the primitive the refusal recommends — and got `InputValidationError: An unexpected parameter 'timeout' was provided`. The suggested remedy was itself learned by failing at it.

_Provenance: nine friction records from the transcript adapter, machine-captured, no narrator. Observed behavior of this product's own agent; grounds usability, not desirability. Unvalidated — for human review._
