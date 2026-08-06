---
type: Solution
source: 'agent-run:autonomous-loop-2026-08-06'
created: '2026-08-06'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

**The idea.** `computeNextWork` excludes any Solution whose status is `shipped` when it builds `solutionsMissingInstruments`. One predicate, no judgement: a solution the operator has recorded as built is not owed a command that fails today, because no such command exists.

**Why this one.** It is the cheapest of the three and it matches what the queue is actually for. `solutionsMissingInstruments` exists to hand a builder something to build; a shipped solution has nothing left to build, so its presence in that list is noise by definition. The same argument already applies elsewhere in the tool — `retiredFromDuplicateScan` shows the sweep is willing to withhold `deferred` nodes from one analysis while every gate still counts them — so this is an existing pattern applied to a status it was not applied to.

**How it compares to its siblings.**
- "Ask a shipped solution for its observed exit code instead of an instrument" keeps the node in the queue and changes the demand. It collects more — a shipped solution ends up with a recorded run — at the cost of a second queue shape and a second thing the pass must know how to answer. This one collects nothing extra and costs a line.
- "Refuse an instrument that passes on arrival" moves the guard to the write boundary and leaves the queue noisy. It catches the bad answer everywhere, including for solutions nobody marked shipped, which is a strictly larger net; but it needs to execute a command to know, which is a much bigger mechanism than a status check.

**Where this fails, stated so it can be judged rather than assumed.** It trusts `status: shipped` completely, and nothing in the tool verifies that status against the repository — a human or an agent sets it from prose. So a solution marked shipped in error disappears from the queue silently, and the tree loses the one prompt that would have surfaced it. The tree already holds a human-required test on exactly this risk ("Audit every shipped solution against the repository before trusting the exclusion"), which is the honest cost of the cheap option. It also does nothing for the 20% figure's real cause if some of the 39 unshown queue entries are unshipped-but-unbuildable for other reasons.

**Cost.** A status predicate in `computeNextWork` and one spec. Comparable to the annotation that would otherwise be written on each shipped node every pass.

⚠️ Unvalidated. Proposed by an unattended pass that was itself being handed the unsatisfiable work, which is a reason to trust the observation and discount the conviction.
