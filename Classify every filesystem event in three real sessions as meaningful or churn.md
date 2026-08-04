---
type: AssumptionTest
source: 'agent:ideation-2026-08-03'
created: '2026-08-03'
evidence: assertion
threshold: >-
  A rule fixed in advance correctly classifies at least 90% of external write
  events, and produces no more than 3 unnecessary invalidations per session.
instrument: npx vitest run test/runner/fs-event-classification.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: feasibility.** A watcher is only useful if meaningful external writes can be told apart from routine churn. Editors write temp files, formatters touch everything on save, and a `git checkout` looks like a thousand external writes at once. A watcher that cannot filter degrades into an alarm nobody reads — the failure mode of every watcher ever built, and the reason this is the riskiest assumption in the candidate rather than the cost of the watcher process.

**The test.** Record every filesystem event during three ordinary working sessions. Write the classification rule *before* looking at the data — ignore paths matched by `.gitignore`, ignore writes this session issued itself, treat a burst above N files in one second as a branch operation rather than N edits — then apply it and score against a hand-labelled ground truth of which events actually invalidated something the agent was holding.

**Why the second condition is the binding one.** A 90% classification rate sounds fine and can still mean several spurious invalidations an hour, which is enough for the signal to be ignored. Capping unnecessary invalidations at three per session is the number that decides whether an agent keeps trusting it.

**What a failure redirects to.** The cheaper approximation named in the solution body — poll the mtimes of only the files this session has read, once before each write batch. That sidesteps classification entirely by only ever asking about files it already cares about, and if this test fails it becomes the stronger candidate.

**A by-product worth keeping:** the same event capture would show how often two writers genuinely overlap, which is direct evidence for [[Two agents sharing my vault can trample each other]], a node currently resting on two anecdotes.

Proposed, not run. Recording a result is a human's `ost-agent result`.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/runner/fs-event-classification.test.ts — Both clauses of the threshold are scored against a fixture: the spec replays the captured filesystem events of three sessions through the classification rule and asserts at least 90% agreement with the committed hand-labelled ground truth and no more than 3 unnecessary invalidations per session. It fails today because no classification rule exists and no event capture is committed to score against.
