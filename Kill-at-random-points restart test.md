---
type: AssumptionTest
status: unvalidated
source: 'agent:P4_assumptions'
created: '2026-07-24'
evidence: assertion
instrument: npx vitest run test/loop/kill-restart-idempotence.test.ts
---
#AssumptionTest #unvalidated #feasibility #evidence/assertion

**Assumption under test (feasibility):** A pass can be killed at any instant and restarted with no corruption, no duplicate nodes, no half-written state, and no stuck locks.

**Proposed test:** Run a pass against a scratch copy of the vault and kill the process at twenty randomly chosen points. After each kill, restart and let it finish. Check the resulting vault for validity, duplicated nodes, truncated files, and orphaned locks.

**Size:** a scripted afternoon against a throwaway vault — never the live one.

**Pre-committed threshold:** 20 of 20 restarts produce a valid vault with zero duplicates and zero partial nodes, and the pass completes. Idempotence is not a percentage; a single failure means the guarantee does not exist.

**Decides:** whether "kill it whenever you like" can be promised to stakeholders, which is the load-bearing claim of the parent opportunity.

Proposed by the agent — to be run by a human against a scratch vault. No results recorded here.

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 instrument: (none) → npx vitest run test/loop/kill-restart-idempotence.test.ts — The bar this node pre-committed is absolute and countable — "20 of 20 restarts produce a valid vault with zero duplicates and zero partial nodes, and the pass completes. Idempotence is not a percentage; a single failure means the guarantee does not exist" — and it names a scratch vault, never the live one, so nothing about it needs a person. The spec builds a throwaway vault, runs a pass, kills the process at twenty seeded interruption points, restarts each time, and after every restart asserts the invariants the CLI already knows how to compute (check passes, no duplicate node files, no truncated body, no orphaned lock) and that the pass reaches completion. It fails today because nothing in the repository interrupts a pass and resumes it: `test/git/stale-lock-recovery.test.ts` covers a crash while holding the lock, which is one of the twenty points, and there is no harness that drives the other nineteen or asserts vault validity across a restart. What it does not settle is the promise the parent opportunity actually wants to make — twenty seeded kill points are the moments an author imagined, and a guarantee of "kill it whenever you like" is a claim about every instant.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/loop/kill-restart-idempotence.test.ts` — No test files found, exiting with code 1
