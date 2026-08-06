---
type: Solution
source: 'USAGE:2026-08-05'
created: '2026-08-06'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Excluding shipped solutions removes items that are genuinely done, not items being dodged]]

**The idea.** `solutionsMissingInstruments` excludes solutions whose status is `shipped`. An instrument must fail against the repository today and pass once the solution is built; for behaviour that already ships, no such command exists, so demanding one asks for something that cannot be supplied.

**Why this shape, and why now.** Four solutions in the 2026-08-06 queue — "Refuse a wiki-link that contains a newline", "Refuse a write whose content is empty or literally undefined", "Refuse a proving command whose exit code cannot report failure", "A result must state what it did not cover" — were each worked by the previous day's sweep, which reached the correct conclusion and wrote it into their histories: the mechanism ships, a spec asserting it would pass on arrival, so status was corrected rather than an instrument invented. All four were back in the queue the next pass. The work was done right and the queue did not notice.

This is the opportunity's mechanism in miniature. The cost is not the four items; it is that every future pass re-reads four solution bodies, re-derives the same conclusion, and either repeats the correction or invents a fake instrument to make the number go down.

**How it differs from its siblings.** The narrowest of the three and the only one that removes items rather than explaining them. It fixes one queue by one rule and touches nothing else; "Each queue reports its delta" makes any queue's movement legible, and "An item a pass declined is suppressed until its reason stops holding" generalises to items that are not shipped.

**Where it fails.** It trusts `status: shipped`, which an agent can set. A solution wrongly marked shipped would vanish from the one queue that would have chased it — so this shifts weight onto a field with no gate behind it, and is only safe while status changes are recorded in `## History` with the reasoning attached, as those four are.

⚠️ Unvalidated. Agent-ideated, from the queue this pass was working.
