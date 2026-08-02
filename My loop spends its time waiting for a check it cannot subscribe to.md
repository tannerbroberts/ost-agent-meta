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
