---
type: AssumptionTest
source: 'agent-ideated:2026-08-02-maintenance-pass'
created: '2026-08-02'
evidence: assertion
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: feasibility** — whether the proposed fields are actually sufficient, not whether they can be captured.

**The assumption under test.** That directory and argv are the missing variables — that a record carrying them becomes reproducible. The 2026-07-27 filing under this node's opportunity supplies one confirmed case where cwd was exactly what was missing, and one case is enough to motivate the candidate but not enough to size it. If cwd and argv close only a small share of real failures, this ships a field that gets filled in dutifully and still leaves the reader stuck — the expensive kind of wrong, because it looks like the problem was solved.

**The test (replay, no new instrumentation).** Take the 10 most recent non-zero exits in `.ost-agent/health/runs.jsonl`. For each, a person who did not run it attempts reproduction **from the record alone**, then classifies the outcome:

- **reproduced** — the record was sufficient as-is;
- **reproduced once cwd and/or argv were supplied** — the candidate would have closed this one;
- **still not reproducible** — and name the variable that was actually missing (env var, git sha, node version, machine load, a concurrent writer, elapsed-time dependence).

That third bucket is the point of the test. The list of named missing variables is more valuable than the score, because it is the specification for whatever the real fix turns out to be.

**Pre-committed threshold.** cwd-and-argv must close **at least 5 of 10**. At 5 or more the candidate ships as designed. Below 5, it is demoted from *the* fix to *a* fix, and the named missing variables from bucket three become the ideation input for sibling candidates under [[I can't tell what a half-finished run actually finished]].

**What a result must also state.** How many of the 10 could not be attempted at all — because the referenced commit is gone, the repo has moved on, or the record is too sparse to even start. Those are not failures of the candidate; they are a separate finding about record retention, and conflating them would flatter the result in one direction or damn it in the other.

**Who runs it.** A human. This pass proposes the design only.
