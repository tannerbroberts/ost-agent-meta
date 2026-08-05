---
type: AssumptionTest
created: '2026-08-05'
evidence: assertion
threshold: >-
  No rollup line expresses instrument coverage as a built percentage, and every
  bucket states its executed count in a position at least as prominent as its
  readiness count.
instrument: npx vitest run test/ost/rollup-execution-first.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**The assumption: the accounting change is expressible without losing information.** The current rollup line reads `built 13% (3/24 runnable), tested 0` — readiness as a moving percentage, execution as a trailing zero. The claim is that these can be reported as two distinct quantities, with the word "built" not applied to either, and that the result is more honest without being less useful.

**Risk category: feasibility, and it is the cheapest node in this branch to settle.**

**Design.** Render the rollup over the current tree and assert no line expresses instrument coverage as a built percentage, and that each bucket's executed count sits at least as prominently as its readiness count. Assert both numbers survive — this must not be achieved by dropping readiness, which is real information about real work.

**Why it is small.** A rendering assertion over a tree that already exists.

**What it does NOT cover, and the node says so itself.** Whether anyone behaves differently. After this ships, exactly as many tests have been run as before; the operator has a more honest dashboard describing the same stall. Whether a stated zero prompts action where a moving percentage did not is a question about a person reading a report, and no spec observes that. Its honest role is as a companion to whichever mechanism actually gets built.
