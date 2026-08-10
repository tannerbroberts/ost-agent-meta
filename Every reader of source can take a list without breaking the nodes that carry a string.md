---
type: Assumption
source: 'TRANSCRIPT:3b9eaea5-d098-4f47-ad0a-65871012d639'
created: '2026-08-10'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion

**The belief, stated so it can be false.** `source` has a small, enumerable set of readers, and each can be widened to a list while a node carrying a plain string keeps behaving exactly as it does now.

The readers are not hypothetical and they are not all in one place: the mapped-ness derivation in `src/processes/tree.ts`, `classifyProvenance` in `knowledge/believability.ts` — which recognises `WEB:` and `INTERVIEW:` prefixes that are *not* evidence ids and must stay honest under a list — the evidence-id-shape check `claimsStoredEvidence`, the near-miss reporter that catches `inbox:note.md` typed against `INBOX:note.md`, and the rung ceiling that caps a node by what its source channel has earned.

That last one is where the belief is most likely to be false, and it is not a plumbing problem. A rung ceiling over a *set* of sources has to answer a question that does not arise for a single source: is a node citing one `stated` record and thirty-nine `assertion` records capped at the weakest, the strongest, or something else? Every answer is defensible and one of them silently promotes nodes.

**Category:** feasibility.

**Why it is the riskiest belief under this solution.** The count saving is obvious and uncontested. What is uncertain is whether the change can be made without opening a hole in the ladder, which is the mechanism the whole tree's credibility rests on.
