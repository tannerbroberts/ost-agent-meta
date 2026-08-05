---
type: Solution
source: 'agent-ideated:2026-08-03-unattended-sweep-unattended-decisions'
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[The decisions a run stops for fall into stable classes that can be settled in advance]]

**Where authority sits: delegated in advance, by class.** The human writes down once — not per question — which kinds of decision a run may settle on its own: reversible and confined to the repo, yes; anything outward-facing, anything that spends money, anything that amends a rule the vault is governed by, no. A run consults the contract at the fork and either proceeds under it or stops and cites the clause that stopped it.

This is a generalization of a mechanism this vault already runs and already trusts. Assumption tests carry a `lane:` set only by a human's `ost-agent lane`, and the agent's own tool can only ever *remove* work from compute's reach. The contract is that idea applied to decisions rather than to tests, with the same asymmetry preserved.

**How it compares to its siblings.** It is the only candidate that actually removes stops rather than rescheduling them, and the only one whose benefit compounds — every question that falls inside a written class is settled for good, not just this run. It is also the only one that requires the human to do work *before* any benefit arrives, and that work is hard: writing a taxonomy of decisions you have not been asked yet.

**Its chief risk: the classes may not carve the real questions.** The seventeen stops this tree has recorded are strikingly non-repeating — what happens to a published npm package, how to resolve a committed merge conflict, whether to close an obsolete PR, what the build loop does when the gate refuses a candidate. If real forks are mostly novel, a contract either stays so abstract that applying it is itself the judgement call, or stays so specific that it covers almost nothing and the run stops anyway. The second failure is safe and disappointing; the first is the dangerous one, because an abstract clause read generously by an eager run is indistinguishable from no contract at all.

**A boundary it must not blur.** The one class that can never be delegated is the class the newest evidence lands in: a decision about the governance of the tree itself. A contract that lets compute rule on what the loop does when the gate refuses a candidate has delegated the gate.

## Definition of done

[[Draft the decision classes from the older half of the stops and test them on the newer half]]

```
npx vitest run test/loop/authority-class-holdout.test.ts
```

Green means classes drawn from the older recorded stops actually classify the newer ones — the holdout that distinguishes a contract from a post-hoc description of what already happened. It settles generalisation, not authority: whether the operator would *grant* the classes this exercise discovers is a consent question, and it is the one [[Ask five operators whether they would let a stated default stand while they are away]] goes after.

## History
- 2026-08-05 unlinked [[Draft the decision classes from the older half of the stops and test them on the newer half]] — moved under [[The decisions a run stops for fall into stable classes that can be settled in advance]] — the belief this test measures now has a node of its own
