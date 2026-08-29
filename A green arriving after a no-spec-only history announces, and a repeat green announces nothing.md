---
type: AssumptionTest
created: '2026-08-22'
evidence: assertion
threshold: >-
  exactly one announcement for a red-then-green and for a no-spec-then-green
  history, and zero for a green-then-green history
instrument: npx vitest run test/telemetry/build-landed-announcement.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.** This is an assertion about which observations produce an event, settled by driving the observation path against fixture nodes.

**Design.** Four histories, one announcement question each:

| Prior observations of the current instrument | Run now | Announce? |
|---|---|---|
| one `**red**` | green | yes — the case `transitioned` already covers |
| one `**no-spec**`, no red | green | yes — the case that is silent today |
| nothing at all | green | refused upstream, so no event to test |
| one `**green**` | green | no — the build already landed once |

The fourth row is the one that keeps the channel worth reading: an announcement per verify run rather than per build turns a rare, meaningful interrupt into a recurring one, which is precisely the habituation failure the sibling assumption is about. A mechanism that cannot tell "built" from "still built" defeats the candidate on feasibility before desirability gets a turn.

**Pre-committed threshold:** exactly one announcement for each of the first two histories, zero for the fourth, and zero duplicate announcements across two consecutive green runs of the same instrument.

**What this does not settle.** Whether the founder keeps reading the interrupts. That is the sibling assumption, "Highlight interrupts keep their signal — the founder keeps reading them rather than tuning them out", and it needs the founder over time, not an exit code. It also says nothing about the announcement's content being useful — only that the right number of them fire.

## Instrument Log
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-24 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-24 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-25 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-26 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-26 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-26 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-27 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-27 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-27 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-27 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-27 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-27 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-28 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-28 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-28 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-28 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-28 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-28 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-28 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-28 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-29 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-29 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-29 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-29 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-29 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-29 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-29 **no-spec** (exit none) `npx vitest run test/telemetry/build-landed-announcement.test.ts` — test/telemetry/build-landed-announcement.test.ts does not exist — no spec was collected, so nothing was measured
