---
type: AssumptionTest
source: 'agent-ideated:2026-08-02-maintenance-pass'
created: '2026-08-02'
evidence: assertion
instrument: npx vitest run test/loop/record-replay-sufficiency.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: feasibility** — whether the proposed fields are actually sufficient, not whether they can be captured.

**The assumption under test.** That directory and argv are the missing variables — that a record carrying them becomes reproducible. The 2026-07-27 filing under this node's opportunity supplies one confirmed case where cwd was exactly what was missing, and one case is enough to motivate the candidate but not enough to size it. If cwd and argv close only a small share of real failures, this ships a field that gets filled in dutifully and still leaves the reader stuck — the expensive kind of wrong, because it looks like the problem was solved.

**The test (replay, no new instrumentation).** Take the 10 most recent non-zero exits in `.ost-agent/health/runs.jsonl`. For each, a person who did not run it attempts reproduction **from the record alone**, then classifies the outcome:

- **reproduced** — the record was sufficient as-is;
- **reproduced once cwd and/or argv were supplied** — the candidate would have closed this one;
- **still not reproducible** — and name the variable that was actually missing (env var, git sha, node version, machine load, a concurrent writer, elapsed-time dependence).

That third bucket is the point of the test. The list of named missing variables is more valuable than the score, because it is the specification for whatever the real fix turns out to be.

**Pre-committed threshold.** cwd-and-argv must close **at least 5 of 10**. At 5 or more the candidate ships as designed. Below 5, it is demoted from *the* fix to *a* fix, and the named missing variables from bucket three become the ideation input for sibling candidates under "I can't tell what a half-finished run actually finished".

**What a result must also state.** How many of the 10 could not be attempted at all — because the referenced commit is gone, the repo has moved on, or the record is too sparse to even start. Those are not failures of the candidate; they are a separate finding about record retention, and conflating them would flatter the result in one direction or damn it in the other.

**Who runs it.** A human. This pass proposes the design only.

## History
- 2026-08-05 instrument: (none) → npx vitest run test/loop/record-replay-sufficiency.test.ts — Reads the 10 most recent non-zero exits from .ost-agent/health/runs.jsonl and asserts each can be reconstructed into an executable invocation from the record alone, requiring at least 5 to carry both cwd and argv. Red today: no reconstruct-from-record helper is exported from the loop step reader at all, and the pre-v0.20.0 lines in the corpus carry neither field, so the assertion fails on both the missing mechanism and the existing data.

## What the instrument does not settle

The instrument `npx vitest run test/loop/record-replay-sufficiency.test.ts` answers only the mechanical half of this test: whether the record carries enough to reconstruct the invocation. A green exit code says the fields are present and sufficient to rebuild a command; it does not say the rebuilt command reproduces the original failure, and it says nothing at all about bucket three — the named variable that was actually missing — which is the part this test's own body calls more valuable than the score.

That naming is a judgement over real failures and stays with a person. So a pass here is necessary and not sufficient: it clears the question "is cwd-and-argv recorded and reconstructable" and leaves "is cwd-and-argv *enough*" exactly where it was.

## Instrument Log
- 2026-08-07 **red** (exit 1) `npx vitest run test/loop/record-replay-sufficiency.test.ts` — No test files found, exiting with code 1
