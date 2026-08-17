---
type: AssumptionTest
source: 'agent:ideation-2026-08-03'
created: '2026-08-03'
evidence: assertion
threshold: >-
  Fewer than 1 false refusal per 50 writes across the 22 captured sessions; and
  every one of the 6 recorded Edit failures is correctly re-labelled as drift or
  not-drift.
instrument: npx vitest run test/git/read-write-hash-drift.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: usability.** The guard's danger is false refusals. If reads and writes are far enough apart in a real session, the fingerprint goes stale far more often than the content is genuinely contested — and an agent that gets refused constantly for changes that did not matter is worse off than one that occasionally guesses wrong.

**The test.** The material already exists: twenty-two mechanically-captured sessions, six of which contain a real Edit failure. Replay their read/write sequences against the file states in git history and count two things — how many *successful* writes a hash guard would have blocked (the false-refusal rate), and whether it correctly separates the six known failures into drift and not-drift.

**Why the second condition is the interesting one.** The whole claim of this candidate is that it distinguishes *you misremembered* from *someone else edited it*, which today's message conflates. A guard with a great false-refusal rate that cannot make that distinction has not delivered the thing it was chosen for. Session `424486ec` — where roughly fourteen files changed within seconds while the agent worked — should come back as drift; the sessions with no concurrent writer should not.

**Why the rate threshold is strict.** One refusal per fifty writes is roughly one per working session. Much beyond that and the agent will start re-reading defensively before every write, which is the cost this candidate was meant to remove.

**Cheapness is the point.** No build, no participants, no live run — twenty-two transcripts and the repo's own history are the whole apparatus.

Proposed, not run. Recording a result is a human's `ost-agent result`.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/git/read-write-hash-drift.test.ts — Replays captured sessions through a read-to-write hash guard and asserts it refuses only the writes whose file actually drifted, naming what drifted; fails today because no hash is carried from read to write.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/git/read-write-hash-drift.test.ts` — No test files found, exiting with code 1
- 2026-08-17 **green** (exit 0) `npx vitest run test/git/read-write-hash-drift.test.ts` — Duration  282ms (transform 18ms, setup 0ms, collect 17ms, tests 53ms, environment 0ms, prepare 26ms)
