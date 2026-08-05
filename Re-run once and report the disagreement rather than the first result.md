---
type: Solution
source: 'agent-ideation:2026-08-02-maintenance-pass'
created: '2026-08-02'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Isolation acquits a flake and convicts a real regression]]

**The idea.** When a timing assertion fails, re-run that test alone and compare. Agreement means red — report it as a real failure. Disagreement means the record says so explicitly: *"failed at 2280ms in suite, passed at 18077ms of margin in isolation — contention, not regression."* The verdict carries its own attribution instead of leaving the reader to re-derive it.

**Why it addresses the need.** It is the only candidate that fixes the *stated* need rather than the underlying flake. The opportunity is not "the test fails sometimes" — it is "I cannot tell which kind of failure this was, so I have to check by hand." This is precisely the check a human performed, twice, on 2026-08-01, and it produced the right answer both times. Automating the thing that already worked is a low-risk move.

**How it differs from its siblings.** The other two try to make the measurement not flake. This one accepts that a wall-clock measurement on a shared box will flake and makes the flake *self-labelling*. It is the only one that keeps the original signal completely intact — if the operation really does get slower, the re-run agrees and the red stands with its full original meaning.

**Where it fails.** It doubles the cost of a failing timing test, which is fine at this scale and would not be in a large suite. More seriously, it is only correct if isolation is a fair test — an operation that is slow *because* of a genuine regression under concurrency would pass in isolation and be labelled a flake, which is the exact wrong answer and would be invisible. It also normalises the flake rather than removing it, and normalising a flake is how a gate stops being read.

**Relationship to the others, stated plainly.** This is not really a competitor. It is the cheapest thing that could work now, and it stays useful underneath either of its siblings — a ratio test or a work-unit test can still fail unexpectedly, and re-run-and-attribute makes any of them more readable. A human choosing here should probably ask which one to build *first*, not which one to build.

**Cost.** Small: retry logic and a message.

⚠️ Unvalidated. Agent-ideated, 2026-08-02.

## Definition of done

[[Check whether isolation correctly acquits a flake and convicts a real regression]]

```
npx vitest run test/runner/flake-attribution.test.ts
```

Green means all three planted scenarios are labelled correctly on 3 of 3 repetitions each: a load-induced flake labelled *contention*, a load-independent regression labelled *regression* and surviving the isolated re-run, and — the scenario that decides the candidate — a regression that manifests only under parallel execution still labelled *regression*. It is red today because no re-run-and-attribute mechanism exists, so nothing returns a label to check.

**Scenario 3 is not negotiable and the spec must not be written to pass without it.** The dangerous case is a false acquittal: an operation slow *because* of a genuine regression under concurrency passes in isolation and gets filed as a flake, silently. The failure this mechanism would introduce is quiet; the failure it removes is loud. A spec that only covered scenarios 1 and 2 would go green on a design that is strictly worse than doing nothing.

**A red result here still leaves something buildable,** which is why this command is worth running before the mechanism is committed to. If scenario 3 cannot be convicted, the honest fallback is already written into the test node: report the disagreement without resolving it — *"failed in suite, passed in isolation; cause not determined"* — keeping the attribution information and dropping the unearned verdict. That is a rewrite of this solution, not a closed branch.

**What green does NOT settle.** That the labels are *useful* to whoever reads them. Correct attribution on three planted cases says nothing about how often the real corpus contains a shape none of the three resemble, and a plant is by construction the shape its author already imagined — the caution [[Do the shipped sweeps actually find a planted instance]] recorded after its own run.

## History
- 2026-08-05 unlinked [[Check whether isolation correctly acquits a flake and convicts a real regression]] — moved under [[Isolation acquits a flake and convicts a real regression]] — the belief this test measures now has a node of its own
