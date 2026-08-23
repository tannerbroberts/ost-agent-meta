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
---
#AssumptionTest #unvalidated #evidence/assertion

**What the spec has to assert.** Build a fixture vault whose recorded history contains three red-to-green instrument flips written in the shapes this product has actually produced across versions, plus a decoy set — a red that stayed red, a `no-spec` run, a status change to `deferred`, an ordinary body edit. Call the digest builder over it. Assert that its top three entries are exactly the three flips, in any order, and that the builder made no model call (no network, no API client constructed).

**Why the decoys are the test.** A digest that returns the three flips out of a fixture holding only three flips has demonstrated nothing. The claim under test is that a flip is *recognisable from the record*, which only means something when the record also holds things that are not flips and look similar. A `no-spec` run is the sharpest decoy: it is an instrument observation that is not a flip, and the product's own permit logic already treats it as its own class.

**Pre-committed bar.** All 3 seeded flips named; 0 non-flip entries in the top 3; 0 model calls. Fixed here, before anything is built, and deliberately allowing the run to come out a failure: two of three, or three of three with a decoy in the list, is a refutation and not a partial pass.

**Lane: compute-only.**

**How red this is today, stated honestly.** No digest builder and no such spec exist, so this command fails today by finding no spec file — the weakest reason a command can fail, and the same reason it would fail for any question written on that path. It is recorded anyway because this test carries a bar fixed in advance, and a bound threshold is what lets a builder work to a definition of done when the spec is still empty. The test is not finished until the spec exists and an assertion in it fails; whoever writes it should expect to be judged on the decoys, not the flips.

**What a green here would not settle.** Only that flips can be got back out of history. It would say nothing about whether those are the events the founder wants to hear about — that is the sibling belief, "What the founder means by highlights is already present in vault history", and it is answerable only by handing him a real digest and asking what it missed. A passing spec here plus an unanswered sibling is a digest that is cheap to build and possibly about the wrong things.
