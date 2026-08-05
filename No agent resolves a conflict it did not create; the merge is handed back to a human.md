---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Conflicts are rare and contested enough that human-only resolution does not flood the operator]]

Conflict resolution becomes a class of decision compute may not take alone. An agent meeting a conflict between its own work and someone else's stops, records both sides, and hands the merge to a human. It may describe the conflict and propose a resolution; it may not commit one.

The reasoning is that a merge conflict is two intentions disagreeing, and an agent has access to one of them. Resolving it means guessing what the other writer meant, and a wrong guess produces something that looks resolved — which is exactly the state that reached a commit here.

**Compared to the alternatives.** The only option addressing the cause rather than the symptom, and it fits the pattern the vault already uses for decisions where being confidently wrong is expensive. It also blocks unattended work at precisely the moment concurrency was supposed to help, and it will stop on trivial conflicts as readily as on serious ones.

**What would make this the wrong pick.** Most conflicts in an append-only Markdown vault are mechanical and safely resolved. A rule that treats all of them as human-only will send a great deal of trivia to the operator, and an operator who is sent enough trivia stops reading it.

Setting this boundary is a human's decision. No pass may grant itself the permission it withholds here, or take it away.

## Definition of done

[[Count how many vault conflicts are mechanical, to see what a human-only rule would actually cost]]

```
npx vitest run test/git/conflict-mechanicality-census.test.ts
```

Green means every conflict in the vault history is classified as mechanically resolvable or not, so the price of the human-only rule is a number rather than a worry. It settles the cost side only. Whether that price is worth paying is the operator's call, and the safety argument for the rule does not depend on the count coming out low.

## History
- 2026-08-05 unlinked [[Count how many vault conflicts are mechanical, to see what a human-only rule would actually cost]] — moved under [[Conflicts are rare and contested enough that human-only resolution does not flood the operator]] — the belief this test measures now has a node of its own
