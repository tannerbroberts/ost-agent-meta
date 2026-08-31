---
type: AssumptionTest
source: 'INBOX:2026-08-11-observed-build-loop-reports-not-merged-on-merged-prs.md'
created: '2026-08-23'
evidence: assertion
threshold: >-
  all 3 seeded red-to-green flips named, 0 non-flip entries in the top 3, and 0
  model calls made
instrument: npx vitest run test/loop/highlights-digest.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**What the spec has to assert.** Build a fixture vault whose recorded history contains three red-to-green instrument flips written in the shapes this product has actually produced across versions, plus a decoy set — a red that stayed red, a `no-spec` run, a status change to `deferred`, an ordinary body edit. Call the digest builder over it. Assert that its top three entries are exactly the three flips, in any order, and that the builder made no model call (no network, no API client constructed).

**Why the decoys are the test.** A digest that returns the three flips out of a fixture holding only three flips has demonstrated nothing. The claim under test is that a flip is *recognisable from the record*, which only means something when the record also holds things that are not flips and look similar. A `no-spec` run is the sharpest decoy: it is an instrument observation that is not a flip, and the product's own permit logic already treats it as its own class.

**Pre-committed bar.** All 3 seeded flips named; 0 non-flip entries in the top 3; 0 model calls. Fixed here, before anything is built, and deliberately allowing the run to come out a failure: two of three, or three of three with a decoy in the list, is a refutation and not a partial pass.

**Who may run it.** Nothing in this question needs a person — it is a spec over a fixture, and the answer is an exit code. The node is nonetheless in the needs-a-person lane, because the lane label is set with `ost-agent lane --set` and no agent surface can move work into compute's reach. Whoever reviews this can relabel it; until then it will be listed as waiting on a human, which understates what it actually needs.

**How red this is today, stated honestly.** No digest builder and no such spec exist, so this command fails today by finding no spec file — the weakest reason a command can fail, and the same reason it would fail for any question written on that path. It is recorded anyway because this test carries a bar fixed in advance, and a bound threshold is what lets a builder work to a definition of done when the spec is still empty. The test is not finished until the spec exists and an assertion in it fails; whoever writes it should expect to be judged on the decoys, not the flips.

**What a green here would not settle.** Only that flips can be got back out of history. It would say nothing about whether those are the events the founder wants to hear about — that is the sibling belief, "What the founder means by highlights is already present in vault history", and it is answerable only by handing him a real digest and asking what it missed. A passing spec here plus an unanswered sibling is a digest that is cheap to build and possibly about the wrong things.

## History
- 2026-08-23 body edited — Removing a "Lane: compute-only." declaration this pass wrote into the prose. The node came back from the sweep in the needs-a-person lane, so the sentence asserted a lane the frontmatter does not carry — exactly the contradiction the lane-conflict rule exists to catch, and nothing on an unattended surface can set the field to match (the permissive call is `ost-agent lane --set`, a human's). Replaced with a statement of what the test needs rather than a label it cannot back. No other claim changed.

## Instrument Log
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-24 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-24 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-25 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-26 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-26 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-26 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-27 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-27 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-27 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-27 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-27 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-27 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-28 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-28 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-28 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-28 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-28 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-28 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-28 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-28 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-29 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-29 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-29 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-29 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-29 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-29 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-29 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-29 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-30 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-30 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-30 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-30 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-30 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-30 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/loop/highlights-digest.test.ts` — test/loop/highlights-digest.test.ts does not exist — no spec was collected, so nothing was measured
