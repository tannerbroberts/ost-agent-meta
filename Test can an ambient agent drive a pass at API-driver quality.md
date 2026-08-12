---
type: AssumptionTest
status: unvalidated
source: 'INBOX:2026-07-22-agent-as-driver.md'
created: '2026-07-25'
evidence: assertion
instrument: npx vitest run test/loop/ambient-driver-parity.test.ts
---
#AssumptionTest #ported-from-ost-agent-vault #evidence/assertion

**Risk category: Feasibility.** Riskiest assumption: an ambient session agent driving via MCP/CLI can complete a full maintenance pass at quality comparable to a dedicated API-keyed driver, with no safety violations.

**Proposed test (small, fast):** Run the same ~10 evidence sets through ambient-driven and API-driven passes; compare faithfulness scores and check for any out-of-allowlist action.

**Pre-committed success threshold:** ambient faithfulness within 10% of API driver; zero safety violations.

_Proposal only — a human runs this with real data. Unvalidated._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-04 instrument: (none) → npx vitest run test/loop/ambient-driver-parity.test.ts — Parity is a comparison between two trees the suite can produce itself — drive one pass over a fixture vault through the ambient path and one through the API-driver path, then assert the resulting node sets and edges match; it fails today because the ambient driver does not exist, so there is nothing to compare against.

## What a green run does not settle

Parity of node sets and edges is the strictest thing a spec can assert here, and it is still only structural. Two passes can produce identical trees whose *prose* differs in quality by a wide margin, and prose is most of what a node is worth. Green therefore means "the ambient driver did not lose or misplace anything", not "the ambient driver writes as well".

The comparison also runs over a fixture vault, where the work is bounded and known. The failure mode this solution actually risks is a long real pass — context exhaustion partway through, or a driver that quietly stops mid-sweep and reports a clean run. A fixture short enough to be a spec will not reach that.

Nothing here touches cost, which is the reason anyone would want an ambient driver in the first place. Whether it is cheaper per pass than the API driver is a measurement, and it is not this one.

## Instrument Log
- 2026-08-06 **red** (exit 1) `npx vitest run test/loop/ambient-driver-parity.test.ts` — No test files found, exiting with code 1
- 2026-08-12 **green** (exit 0) `npx vitest run test/loop/ambient-driver-parity.test.ts` — Duration  3.01s (transform 180ms, setup 0ms, collect 303ms, tests 2.49s, environment 0ms, prepare 33ms)
