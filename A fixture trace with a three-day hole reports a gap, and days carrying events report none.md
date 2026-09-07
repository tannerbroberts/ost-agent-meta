---
type: AssumptionTest
source: 'agent-ideation:2026-09-07-unattended-sweep'
created: '2026-09-07'
evidence: assertion
threshold: >-
  a gap is reported for all 3 seeded dark days and for 0 of the seeded active
  days
instrument: npx vitest run test/mcp/liveness-line.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: feasibility.**

**The design.** Build a fixture vault whose `usage/events.jsonl` reproduces the shape actually observed here: events on a run of consecutive days, then three consecutive days with none, then events again. Declare a `loop.cadence` of `1h`. Run `computeNextWork` over it and assert that the response carries a liveness figure, that it flags the three-day hole, and that it flags none of the days carrying events. Seed one further case that separates this test from a mere date-arithmetic check: a day on which a firing recorded a single invocation and nothing else. That day must NOT be reported as a gap, because it is the case the parent assumption names as the way this goes wrong.

**Pre-committed bar, stated before running:** a gap is reported for all 3 seeded dark days and for 0 of the seeded active days. A rule that flags everything has not distinguished anything, and a rule that flags the single-invocation day is reporting a healthy firing as an outage, which is the failure mode that makes the line worth ignoring.

**What kind of red this is, said plainly rather than left for the log to reveal.** `test/mcp/liveness-line.test.ts` does not exist, so this command is red today for the weakest available reason — it would be equally red under any question written on that filename, and `runInstrument` will file it as `no-spec` rather than as a measurement. That is the strongest red this surface can author, for two reasons established first-party on this tree: writing the failing assertion needs a write grant on the product repository, which an unattended sweep does not hold and should not; and `INSTRUMENT_FORMS` anchors the grammar at `npx vitest run <file>.test.ts` with nothing permitted after the filename, so the alternative of narrowing an existing green spec with a `-t` filter is not merely unwritten here but inexpressible. The bound threshold above is what carries a builder across that gap.

**The spec's home, so a builder does not have to find it.** `test/mcp/next-work.test.ts` already covers `computeNextWork` and passes today, which is why this instrument cannot point at it — a green instrument is refused for measuring nothing. The new file belongs beside it, and the module to change is `src/mcp/next-work.ts`, where the response's existing counters are assembled.

**What a green here does not settle, and it is most of the question.** Only that the computation is correct against a fixture. It says nothing about whether a real operator reads the line, notices it, or acts on it — that is this candidate's own kill criterion and no exit code observes it. It says nothing about desirability or viability, and nothing about whether this candidate beats either sibling. Feasibility answered mechanically leaves the other three risk categories exactly where they were.

Proposed only. This pass did not run it.
