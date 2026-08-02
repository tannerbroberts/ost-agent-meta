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
