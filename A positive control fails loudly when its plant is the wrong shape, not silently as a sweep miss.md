---
type: Assumption
source: 'agent-ideation:2026-08-09-unattended-sweep'
created: '2026-08-10'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Plant a deliberately mis-shaped instance and require the control to report a bad plant, not a miss]]

**The belief, stated so it can be false.** A positive control can tell the difference between a check that went blind and a plant that was never the shape the check looks for, and reports the two differently.

**Why this node exists, and it is not a fresh idea.** The test beneath this solution already ran on 2026-07-27 — 12 plants, 12 found, 0 checks blind — and by its own pre-commitment that result made the solution "a belt-and-braces addition that can wait." But the run surfaced something its threshold was not measuring, recorded on the solution: **all three apparent misses were defects in the plants, not in the checks.** The solution body draws the conclusion and then leaves it hanging as a recommendation with no node: "Whatever eventually gets built here should carry an assertion that the baseline is clean *and* that the plant is the shape the rule matches."

That recommendation is a second belief, distinct from the one already tested. The tested belief was "a positive control would fire on the sweeps that shipped." This one is "a positive control does not lie in the other direction." They fail independently, and only the first has ever been checked.

**Why it could be false.** A positive control has exactly one output an operator reads: found or not found. A plant that the rule does not match produces *not found*, which is indistinguishable at that output from a check that has gone blind — and it is the more alarming of the two readings, so it wins attention it has not earned. The solution's own stated failure mode is adjacent but not the same: "a control chosen from the same source the sweep reads can be blind in the same way." That is a false *negative*. This is a false *alarm*, and the 2026-07-27 run produced three of them and zero of the other, which is evidence about which failure mode actually occurs here.

The cost of getting it wrong is specific: a false alarm on a positive control sends someone to investigate a sweep that is working, and the second time it happens the control stops being believed. A control nobody believes is worse than no control, because it was paid for.

**Why it could be true.** If plants are constructed by the same code that defines what the rule matches, a mis-shaped plant is unconstructible and the belief holds trivially. Whether that is how it would be built is the design question the test is really probing.

**Grounded against the repository, 2026-08-09.** `src/ost/census.ts` implements the independent-denominator family this solution's siblings came from — `reconcileWithGit` shells out to `git ls-files` precisely so a broken walk cannot define its own denominator, and `reconcileWithUsage` reads the usage trace as a third source. Its header states the trap in the same terms this solution does: "a denominator computed by the same broken walk excludes the same files the counter excluded, so the ratio reads 100% and says nothing." So the codebase already takes independence seriously. What it has nowhere is a **plant**: no seeding mechanism exists in `census.ts` or `stranded.ts`, and `test/ost/` holds `blind-sweep-replay.test.ts` and `stranded-evidence-census.test.ts` but no positive-control spec. The mechanism is absent by reading, not by assumption.

⚠️ Unvalidated. Agent-ideated from an observed run.
