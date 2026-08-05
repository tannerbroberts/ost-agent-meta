---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Two real vaults can be merged with few enough conflicts for a person to settle them]]

There is no central inbox. An operator who wants to benefit from another instance's experience arranges an exchange with that instance directly — a pull from a git remote they were given access to, on terms the two of them set. Learning spreads peer to peer, and nobody has to trust an operator they have not chosen to trust.

Given that every vault is already a git repository, most of this exists: the exchange is a remote and a fetch, and the merge question is the same one the tree already has to answer for two agents sharing one vault.

**Compared to the alternatives.** The only option requiring no consent from anyone to a party they cannot see, which makes it the easiest to adopt and the only one that works for an operator who will never report outward under any terms. It scales badly on purpose — nothing aggregates, so nobody ever sees the pattern across a hundred instances, which is precisely what the central inbox is for. Refusal-only reporting sits between the two.

**What would make this the wrong pick.** Peer exchange gives the tool's author nothing. If the point of gathering experience is to improve the product rather than to enrich individual trees, this route structurally cannot serve it, however well it serves the operators.

## Definition of done

[[Merge two real vaults as a dry run and count the conflicts a person has to settle]]

```
npx vitest run test/ost/vault-merge-conflict-census.test.ts
```

Green means merging the two existing vaults into a scratch tree produces at most 5 conflicts that a stated rule cannot settle. It is red today because nothing merges two vaults or partitions conflicts into rule-settleable and judgement-requiring.

**Counting only the conflicts a person has to think about is the measurement, not a convenience.** Raw conflict count says nothing: a merge with two hundred collisions that a rule resolves cleanly is cheap, and a merge with six that each need a ruling is not. The assumption under test is that peer exchange is cheap *in practice* — if every exchange costs an afternoon of merge work, nobody does it twice and the federation has no members.

**This is the easiest possible case and green should be discounted accordingly.** The two vaults share an author, a schema version, and a naming style. Two vaults from unrelated teams would collide far more, and nothing in this command reaches that. A red result here is therefore much more informative than a green one: it would mean the mechanism fails on the most favourable input that exists.

**What green does NOT settle.** It measures merge cost, not merge value — whether a tree that absorbed another team's nodes is better than the one it started as is a judgement no conflict census touches, and it is the question a federation actually lives or dies on.

## History
- 2026-08-05 unlinked [[Merge two real vaults as a dry run and count the conflicts a person has to settle]] — moved under [[Two real vaults can be merged with few enough conflicts for a person to settle them]] — the belief this test measures now has a node of its own
