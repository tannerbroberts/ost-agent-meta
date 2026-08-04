---
type: AssumptionTest
source: 'agent:ideation-2026-08-02'
created: '2026-08-02'
evidence: assertion
threshold: >-
  At least 8 of the last 10 versions cut on `main` were resolvable from the
  registry within 24 hours of their commit. At 7 or fewer, the registry is not a
  path improvements travel down and the candidate is killed rather than
  repaired.
instrument: npx vitest run test/release/registry-propagation-lag.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: feasibility.** The assumption is not "can an instance resolve `@latest`" — it obviously can. It is that **the registry is a path improvements actually travel down**, so that resolving latest resolves something new.

**Why this is the riskiest assumption under its solution.** This vault has already recorded the counter-evidence in passing, five passes running, without ever testing it as a claim: `npm whoami` returning `ENEEDAUTH`, four releases cut and unpublished, and `npx -y ost-agent@latest mcp` resolving to 0.9.0 while v0.10.0 through v0.13.0 sat on `main`. If that stretch is representative rather than a bad week, a pull-at-start mechanism propagates nothing and the build is wasted.

**The test, small and retrospective.** Take the last ten version tags or version bumps on `main`, and for each ask two questions from the record alone: was it ever published, and how long after the commit. Compare the resolved-latest an instance would have got on each of those days against the version that existed. No build, no operator, no new instrumentation — the answer is entirely in git history and the registry's own version list, which is why this is the cheapest disconfirmer in this branch.

**Pre-committed bar (also in the `threshold` field, so a reader does not have to trust prose):** at least 8 of the last 10 versions resolvable from the registry within 24 hours of their commit. At 7 or fewer, the candidate is killed rather than repaired — the fix would be a publish credential and a release discipline, which is a different opportunity from this one.

**What a supported result would and would not license.** Supported means the registry carries releases promptly, so pull-at-start is worth building; it would say nothing about whether halting a stale instance is the right response to skew, which is a separate judgement about unattended operation. Refuted means the propagation problem is upstream of any mechanism on the instance side, and the tree should stop ideating instance-side pulls until publishing is solved.

**What it deliberately does not cover:** the ten-release window is this product's own release history and one publisher. It measures this project's discipline, not the registry's reliability in general, and a future operator publishing their own fork would need their own reading.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/release/registry-propagation-lag.test.ts — The node states the answer is "entirely in git history and the registry's own version list", so the spec walks the last ten version bumps on `main`, resolves each against the committed registry version snapshot, computes the lag between commit and publish, and asserts at least 8 of 10 were resolvable within 24 hours. It fails today because nothing in the repository computes propagation lag and no registry snapshot is committed to score against.
