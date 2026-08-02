---
type: AssumptionTest
source: 'agent-ideated:2026-08-02-maintenance-pass'
created: '2026-08-02'
evidence: assertion
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: viability.** Whether the rule's cost lands on the party that can least afford it.

**The assumption under test.** That refusing to release from unpushed history blocks mostly bad releases and few good ones. The candidate carries a specific worry: because push and publish are both gated by the credential in [[Every run ends blocked on a credential only I hold]], a strict push-first rule makes the credential holder mandatory for every release — on a project whose stated constraint is [[I need the tree's output to be actionable by compute alone, because my hours don't exist]]. If the rule mostly blocks releases that were fine, it converts an occasional coordination problem into a permanent human dependency.

**The test (replay, no build, no publish).** For every release in the project's history, reconstruct from git whether the releasing tree was ahead of, behind, or diverged from `origin/main` at the moment of release. Classify each: **would have been allowed**, or **would have been refused**. Then a human judges each refusal against one question: **was this release actually problematic, or was it fine and merely unpushed?**

**Pre-committed threshold.** Of the releases the rule would have refused, **at least 50% must be judged genuinely problematic**. Below 50%, the rule blocks more good releases than bad ones and the candidate is closed in favour of its registry-checking sibling, which allows the divergence and fixes only the number.

**The second number, which matters as much as the threshold.** Total refusals as a share of all releases. Even at a perfect 100% precision, a rule that stops one release in two makes the credential holder a participant in half of all releases, and that is the trade the operator is actually being asked to accept. A result that reports precision without reporting frequency has not answered the question this test was written for.

**And the motivating case, checked explicitly.** Would the rule have prevented the 2026-07-26 near-collision? The builder's work was two commits ahead of origin and unpublished, so on the face of it yes — but confirm rather than assume, because the loop's release came from a different tree that may itself have been in sync, in which case the rule constrains only one of the two trains and the collision survives it.

**Who runs it.** A human, from git history. Nothing is published.
