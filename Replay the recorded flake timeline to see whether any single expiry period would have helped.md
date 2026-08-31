---
type: AssumptionTest
source: 'TRANSCRIPT:785ea509-96b9-4225-b45a-babd5321aafc'
created: '2026-08-05'
evidence: assertion
threshold: >-
  One expiry period exists that fires after every recorded flake was resolved
  and before it was forgotten, with zero firings against an unresolved flake.
instrument: npx vitest run test/telemetry/quarantine-expiry-period.test.ts
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: feasibility.**

The mechanism is not the risk here — an expiry date is trivial to implement. The risk is the **period**, and it is empirical rather than arguable. Too short and the suite goes red on a timer with nothing changed, which this vault's own reasoning says is the worst outcome available: an operator who learns to skip a report misses the real one. Too long and it never fires before the flake is forgotten anyway, which is the state this candidate exists to prevent.

**Design.** Reconstruct the timeline of every flake on record — for the known case, first observed 2026-08-01 (two friction notes naming `test/mcp/wall-clock-budget.test.ts`), still being hand-excluded 2026-08-04, resolution date read from git. Sweep candidate expiry periods across the range and, for each, count firings that would have landed on an unresolved flake against firings that would have usefully forced the question. Assert a single period satisfies both clauses.

**Why it is small.** The dates are in the friction notes and the commit history.

**Why a red here is likely and useful.** The recorded sample is one flake. A period that "works" on one case is fitted to it, and the honest reading of a green on n=1 is that nothing was learned. The threshold is written to require zero bad firings precisely so that a thin sample fails rather than flatters — if the record cannot support a period, the finding is that this candidate needs more history before it can be tuned, and it should not ship on a guessed number.

**What it will not cover.** Whether an operator renews a lapsed quarantine thoughtfully or reflexively is a behaviour no replay can see, and it is the thing that decides whether expiry creates pressure or just ceremony.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/telemetry/quarantine-expiry-period.test.ts` — No test files found, exiting with code 1
- 2026-08-31 **green** (exit 0) `npx vitest run test/telemetry/quarantine-expiry-period.test.ts` — Duration  276ms (transform 26ms, setup 0ms, collect 23ms, tests 3ms, environment 0ms, prepare 38ms)
