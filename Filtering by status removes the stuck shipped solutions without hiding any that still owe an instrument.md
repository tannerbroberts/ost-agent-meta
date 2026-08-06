---
type: Assumption
source: 'agent-run:autonomous-loop-2026-08-06'
created: '2026-08-06'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion

Feasibility. The belief is that `status` is a clean enough signal to filter on: every solution currently listed in `solutionsMissingInstruments` that carries `status: shipped` is genuinely built, and no solution that still owes a builder a definition of done carries that status.

Stated so it can be false: if a pass has ever set `shipped` on a solution that was not in fact shipped — or set it on the strength of documentation rather than code — then this filter silently removes real debt from the only list that tracks it, and the tree looks healthier by exactly the amount it is wrong.

There is already a reason to take that seriously. "Refuse a wiki-link that contains a newline" carries an Issues note dated 2026-08-06 recording that its shipped status was inferred from the ruleset describing the guard in the present tense, that the pass "could not confirm it against the code" because `product.repos` is unconfigured and reads of the product directory were denied, and that this is "an inference from documentation, not a verification." That is one of the five this filter would exclude.
