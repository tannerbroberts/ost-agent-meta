---
type: Solution
source: 'agent-ideation:2026-08-02-maintenance-pass'
created: '2026-08-02'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Check whether isolation correctly acquits a flake and convicts a real regression]]

**The idea.** When a timing assertion fails, re-run that test alone and compare. Agreement means red — report it as a real failure. Disagreement means the record says so explicitly: *"failed at 2280ms in suite, passed at 18077ms of margin in isolation — contention, not regression."* The verdict carries its own attribution instead of leaving the reader to re-derive it.

**Why it addresses the need.** It is the only candidate that fixes the *stated* need rather than the underlying flake. The opportunity is not "the test fails sometimes" — it is "I cannot tell which kind of failure this was, so I have to check by hand." This is precisely the check a human performed, twice, on 2026-08-01, and it produced the right answer both times. Automating the thing that already worked is a low-risk move.

**How it differs from its siblings.** The other two try to make the measurement not flake. This one accepts that a wall-clock measurement on a shared box will flake and makes the flake *self-labelling*. It is the only one that keeps the original signal completely intact — if the operation really does get slower, the re-run agrees and the red stands with its full original meaning.

**Where it fails.** It doubles the cost of a failing timing test, which is fine at this scale and would not be in a large suite. More seriously, it is only correct if isolation is a fair test — an operation that is slow *because* of a genuine regression under concurrency would pass in isolation and be labelled a flake, which is the exact wrong answer and would be invisible. It also normalises the flake rather than removing it, and normalising a flake is how a gate stops being read.

**Relationship to the others, stated plainly.** This is not really a competitor. It is the cheapest thing that could work now, and it stays useful underneath either of its siblings — a ratio test or a work-unit test can still fail unexpectedly, and re-run-and-attribute makes any of them more readable. A human choosing here should probably ask which one to build *first*, not which one to build.

**Cost.** Small: retry logic and a message.

⚠️ Unvalidated. Agent-ideated, 2026-08-02.
