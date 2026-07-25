---
type: AssumptionTest
source: 'agent-run:autonomous-loop-2026-07-25-pass4'
created: '2026-07-25'
evidence: assertion
---
#AssumptionTest #unvalidated #desirability #evidence/assertion

**Assumption under test (desirability/value).** That forcing a runner to write what
their test did not cover changes what a *later* reader concludes from the result —
rather than producing a line of boilerplate that everyone learns to skip.

**Why it is the riskiest assumption under this solution.** The feature is already
shipped, so feasibility is settled and cost is known. What is not known is whether it
works on a human. Required free-text fields have a strong tendency to decay into
ritual: `--by` survives because it is a name and there is only one right answer, but
"what this did not cover" has infinitely many acceptable-looking answers and the
cheapest is "n/a". If that is what people write, this has added friction to the one
command humans are already reluctant to run, and bought nothing.

**Proposed test.** Take six recorded results — three with a substantive uncovered
statement, three with a hollow one — and put them cold in front of a reader who did
not run them. Ask a single question per result: *what would you now be willing to
build on this?* Do not tell them the field exists.

**Pre-commit before looking:** readers must draw materially narrower conclusions from
the substantive three than from the hollow three, in at least 4 of 6 pairings.
Uniform confidence across both sets refutes this — it would mean readers are not
reading the field, and the requirement is friction with no payoff.

**What it does NOT test.** Whether runners *write* good statements when unobserved,
which is the other half and needs real usage over time, not a sitting.

**Lane: humans-required, and obviously so** — it needs a reader from outside the
building, and the whole point is that they did not run the test themselves. Left for
a person to file rather than flagged mechanically, because the flag would be the
agent classifying its own feature's gate.

⚠️ Proposed only — the agent does not run tests or record results.
