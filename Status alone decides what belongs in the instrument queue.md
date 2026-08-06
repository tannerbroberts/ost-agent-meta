---
type: Assumption
source: 'agent-run:autonomous-loop-2026-08-06'
created: '2026-08-06'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Filter the queue on shipped and count what is still unsatisfiable]]

**The belief, stated so it could be false.** Every solution currently in `solutionsMissingInstruments` that cannot be given a red-now instrument is there because it is shipped — so filtering on `status: shipped` empties the unsatisfiable part of the queue and leaves only work a builder can act on.

**Kind.** Feasibility.

**How it could turn out false.** This pass saw 25 of 64 entries and found 5 shipped ones. If the other 39 contain solutions that are built but never marked shipped, or solutions whose behaviour is not a spec-shaped thing at all — the pricing and positioning candidates in the same list, like "Charge per assumption test designed and run to a pre-committed threshold", are the obvious case — then a status predicate removes 5 items from a queue of 64 and the operator's complaint survives almost untouched. The market-shaped entries are the strongest reason to doubt: nothing about them is shipped, and no spec file will ever settle them, so they will sit in the queue after this fix exactly as they do now.

**Why it is the riskiest one here.** The solution is cheap and obviously correct as far as it goes; the only real question is whether "as far as it goes" is a fifth of the problem or the whole thing.
