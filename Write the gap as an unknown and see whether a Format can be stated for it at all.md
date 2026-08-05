---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  A Format can be stated that describes an answer's shape without reducing to a
  resource claim.
instrument: npx vitest run test/ost/unknown-format-required.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that the gap between the affordable goal and the real one is a knowledge gap rather than a resource gap. If what stands in the way is money or time, framing it as darkness misdescribes it — a constraint is not an unknown, and dressing one as the other buys a tidy entry and no progress.

**Risk category: feasibility.** The Format section is the discriminator: an unknown that cannot say what a valid answer looks like is not an unknown.

**Design.** Attempt to write the unknown in full — Format, Methodology, Rationale — for the actual gap in this vault. If a Format can be stated that is not simply "we would have more time", the framing holds. If every attempt reduces to a resource statement, it does not.

**Why it is small.** One node's worth of writing, and the attempt itself is the result.

**What it will not cover.** One gap in one vault. A Format that can be written says the framing is available here, not that it generalises.

## History
- 2026-08-05 instrument: (none) → npx vitest run test/ost/unknown-format-required.test.ts — The test names the Format section as its discriminator — "an unknown that cannot say what a valid answer looks like is not an unknown" — but nothing currently enforces that, so an Unknown can be created with the section absent and the discriminator never bites. This asserts it: creating an Unknown without a non-empty `## Format` is refused at the tool boundary, and `ost_next_work` reports a missing Format in that unknown's `gaps` rather than counting it as contract-complete. Missing-spec red, not assertion red — this pass cannot read the repo, so the file is absent; a builder should write it against the real create path so it goes red on an accepted Format-less Unknown. It does not settle this vault's actual gap: whether a Format can be stated for the affordable-goal gap without reducing to "we would have more time" is a semantic judgement no exit code makes, and it stays with a human.
