---
type: AssumptionTest
status: unvalidated
source: 'agent-ideated:2026-08-02-maintenance-pass-3'
created: '2026-08-02'
evidence: assertion
threshold: >-
  Full question set answered in under 10 minutes AND at least 2 answers are
  facts not already recoverable from the vault; otherwise the recurring cadence
  is killed in favour of a one-time manifest.
instrument: npx vitest run test/config/resource-question-recoverability.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**The assumption under test (viability / usability):** that asking is worth its price. The cost is human minutes — the resource this operator has already declared they do not have — so the question is whether a bounded interview returns facts that no cheaper mechanism could have produced, fast enough that a recurring cadence is tolerable rather than a nag.

**The test:** put the resource question set to the operator once, in one sitting, timed end to end. Then, for each answer, check whether that fact was already recoverable from this vault by someone reading it carefully.

**Pre-committed before running:** the full set must be answered in under ten minutes, and at least two answers must be facts not already recoverable from the vault. Over ten minutes, or fewer than two new facts, kills the recurring cadence — a one-time manifest would then dominate it on cost.

**What it deliberately does not cover:** the decay half of the mechanism, which is the part this candidate exists for. A single sitting cannot show that an expiring answer beats a permanent one; that needs two sittings separated by enough real time for something to change, and it should not be claimed from this result.

**This one needs a person.** It cannot be replayed from the record, because the thing being measured is what a human says and how long they take to say it.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/config/resource-question-recoverability.test.ts — Asserts, for each standing resource question, whether the vault can already recover the answer without asking — the count that decides whether the cadence is worth the operator's time; fails today because no such question set is declared.
