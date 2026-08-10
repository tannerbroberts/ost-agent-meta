---
type: Solution
source: 'agent-run:autonomous-loop-2026-08-09'
created: '2026-08-10'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

**The idea.** `computeNextWork` skips any Opportunity whose status is `deferred` when it builds `underservedOpportunities` — the same predicate it already applies when it builds `retiredFromDuplicateScan`.

**Why this one, and why it is not a fourth restatement of its siblings.** The three siblings all argue about the *instrument* queue and the status `shipped`. This is the *under-served* queue and the status `deferred`, and it was observed on 2026-08-09 as the single remaining entry in that queue: "Want proof no hijackable capability even exists", reported as having 2 solutions and needing 3, while carrying `status: deferred` and a History recording that deferral as a **human-authorized merge** into "Fear the agent could take a destructive, irreversible action".

**What makes this cheap to argue for.** The same `ost_next_work` response that demanded solutions for that node also listed it under `retiredFromDuplicateScan` with the reason "status: deferred — retired, withheld from the duplicate scan". The tool already holds the fact, already computes the exclusion, and already applies it — to one analysis. This is not new logic; it is an existing predicate reaching one more caller. That is the same argument the sibling "Drop shipped solutions from the instrument queue" makes about `retiredFromDuplicateScan`, applied to the status that filter was actually built for.

**Why the harm is worse here than in the shipped case.** An unsatisfiable instrument request wastes a pass's attention. This one invites a pass to **undo a human decision**. The remedy the queue proposes — ideate a third solution — would resurrect a branch a human deliberately retired and relinked elsewhere, and an unattended pass following the instruction literally would do exactly that. The 2026-08-09 sweep declined, but declining required reading the node's History; nothing in the queue entry itself said the node was retired.

**How it compares to the more general alternative.** The structural fix is one disposition filter computed once and consumed by every analysis, so no future analysis can be written that forgets it. That is strictly better and strictly larger: it fixes the shipped case, the deferred case, and cases nobody has hit, at the cost of refactoring every consumer. This candidate is one predicate in one place and fixes the instance that was observed. They are not exclusive — this is the patch, that is the design — and a human choosing between them is choosing how much of the pattern to buy at once.

**Where this fails, stated so it can be judged rather than assumed.** `deferred` is also how this vault records "not now" for work that was never settled by anyone — the ruleset names it as the marker for abandonment. Excluding it from the under-served count means a node someone parked temporarily stops being offered for ideation, and nothing else will surface it. The sibling risk on the shipped filter ("a solution marked shipped in error disappears silently") applies here in the same shape, and the honest version of this candidate needs the deferred set to be visible somewhere the operator actually looks.

**Cost.** A status predicate in one queue builder and one spec.

⚠️ Unvalidated. Proposed by the unattended pass that was itself handed the unsatisfiable item, which is a reason to trust the observation and discount the conviction.
