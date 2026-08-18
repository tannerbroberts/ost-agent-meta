---
type: AssumptionTest
source: 'agent-ideated:2026-08-02-maintenance-pass'
created: '2026-08-02'
evidence: assertion
instrument: npx vitest run test/release/registry-derived-version.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: feasibility.** Whether the rule would have produced correct numbers on real history.

**The assumption under test.** That taking the maximum of the published registry version and the tagged `origin/main` version, then incrementing, produces the right next number every time. It sounds tautological and is not: prereleases, a version yanked from the registry, a tag that exists locally but was never pushed, and the very first publish of a package all break the simple maximum in different directions.

**The test (pure replay, nothing is published).** Reconstruct the release history of `ost-agent` from the registry and from git tags — every version from the first through v0.19.0 and whatever has shipped since. For each release in order, compute what the rule *would* have chosen given the registry and `origin/main` state at that moment, and compare it to what was actually chosen. Record every disagreement and classify it: **rule was right and history was wrong**, **rule was wrong**, or **both defensible**.

**Pre-committed threshold.** **Zero cases where the rule was wrong.** This is a stricter bar than the other tests on this branch and deliberately so — a version number is the one artefact in this product that cannot be corrected append-only once published. A single wrong choice on historical data closes the candidate.

**The case the replay must specifically include.** The 2026-07-26 near-collision: the builder's unpushed local work at what became v0.19.0, against the loop's independently-released v0.18.0. The rule must be shown choosing v0.19.0 for the second train without a human rebasing. If it cannot be demonstrated on the one incident that motivated the whole branch, nothing else in the replay matters.

**What a result must also state.** What the rule does when the registry is unreachable, and whether that path is distinguishable from "nothing published yet." The solution names this as its failure mode; a result that does not exercise it has not covered the candidate.

**Who runs it.** A human, or an attended session with registry read access. No publish rights needed — this test never writes.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/release/registry-derived-version.test.ts — Replays every past release and asserts a registry-derived next version never collides with one already published; fails today because the number comes from the local file, which is how two trains picked the same one.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/release/registry-derived-version.test.ts` — No test files found, exiting with code 1
- 2026-08-18 **green** (exit 0) `npx vitest run test/release/registry-derived-version.test.ts` — Duration  207ms (transform 18ms, setup 0ms, collect 15ms, tests 3ms, environment 0ms, prepare 28ms)
