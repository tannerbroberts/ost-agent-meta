---
type: AssumptionTest
source: 'agent-ideated:2026-08-03-unattended-sweep-unattended-decisions'
created: '2026-08-03'
evidence: assertion
threshold: >-
  At least 8 of 10 decisions accepted without reversal, AND all ten reviewed in
  one sitting of 30 minutes or less. Fewer than 6 accepted, or a review that
  does not happen within a week of being offered, kills the candidate.
---
#AssumptionTest #unvalidated #evidence/assertion

**The assumption under test (desirability, and the viability of the review itself):** that an operator shown decisions already taken will ratify most of them, and will actually read them. Both halves are load-bearing and the second is the one that usually goes unmeasured. A mechanism whose safety depends on a review that never happens has not made the decision safe; it has made it deniable.

**The test.** Reconstruct ten of the recorded forks as this candidate would have handled them: for each, the option the run would have taken, the assumption it proceeded under, what it would have done had the answer been otherwise, and the reversal price now versus later. Present all ten to the operator in one sitting. Record two things: how many they accept as-taken, and how long the sitting runs, measured — not estimated afterwards.

**Pre-committed before running, so this can come out a failure:** at least 8 of 10 accepted without reversal, **and** all ten reviewed in a single sitting of 30 minutes or under. Fewer than 6 accepted kills the candidate outright — at a 40% reversal rate the run is not proceeding under assumptions, it is guessing and billing the human for the cleanup. A review that never happens within a week of being offered also kills it, and that outcome is more informative than a low acceptance rate: it is the failure the candidate's own body names as strictly worse than stopping.

**A result worth separating out.** If acceptance is high but the sitting runs long, the mechanism is sound and the presentation is not — that is a fixable finding and should be recorded as such rather than as a pass. The reversal-price field exists precisely so the operator can triage, and a 30-minute overrun on ten decisions is evidence that the field is not doing that job.

**This one needs a person by construction and cannot be run unattended.** The measurement *is* what the operator ratifies and how long they spend; there is no artifact in the vault that stands in for it. It also has a population problem this vault should state rather than discover: there is one operator, so a pass measures this operator's tolerance, not an operator's. A human should decide whether that is worth running now as a founder-calibration exercise or held until a second operator exists — the same question already recorded against [[Offer the deposit prompt and count who comes back a second time unasked]].

**What it deliberately does not cover.** Whether the reversal price the run states is *accurate*. This test measures whether the operator accepts the decisions; it is silent on whether the undo really costs what the record claims, and a mechanism that systematically under-prices its own reversals would pass this test cleanly.
