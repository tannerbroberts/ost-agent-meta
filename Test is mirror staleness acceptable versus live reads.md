---
type: AssumptionTest
status: unvalidated
source: 'INBOX:2026-07-22-adapter-reality.md'
created: '2026-07-25'
evidence: assertion
instrument: npx vitest run test/adapters/mirror-staleness.test.ts
---
#AssumptionTest #ported-from-ost-agent-vault #evidence/assertion

**Risk category: Viability.** Riskiest assumption: the freshness lag and sync overhead of a local read-only mirror are acceptable trade-offs for the extra isolation (vs reading live systems).

**Proposed test (small, fast):** For one project, build the tree from a mirror and from live reads; compare quality/latency, and ask operators the maximum staleness they'd tolerate.

**Pre-committed success threshold:** tree quality unaffected and the required sync lag falls within operators' stated acceptable staleness.

_Proposal only — a human runs this. Unvalidated._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 instrument: (none) → npx vitest run test/adapters/mirror-staleness.test.ts — Staleness cannot be judged acceptable or otherwise until it is a number the mirror reports, and there is no mirror. This asserts that: every mirrored record carries the time it was fetched, a read from the mirror returns that age alongside the data, and a record older than the configured bound is served with an explicit stale marker rather than silently — so a consumer can never mistake an old read for a live one. Missing-spec red, not assertion red — no mirror exists, so the command fails on a missing file; a builder should write it against the real adapter read path so it goes red on an unmarked stale record. It does not settle whether the staleness is ACCEPTABLE, which depends on what a team is deciding with the data, and is a person's call.

## Instrument Log
- 2026-08-06 **red** (exit 1) `npx vitest run test/adapters/mirror-staleness.test.ts` — No test files found, exiting with code 1
- 2026-08-23 **green** (exit 0) `npx vitest run test/adapters/mirror-staleness.test.ts` — Duration  547ms (transform 69ms, setup 0ms, collect 101ms, tests 40ms, environment 0ms, prepare 57ms)
