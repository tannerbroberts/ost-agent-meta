---
type: Solution
source: 'agent-ideation:2026-08-02-maintenance-pass'
created: '2026-08-02'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A push-first rule would have blocked few enough past releases to be adoptable]]

**The idea.** The release path refuses to run when the working tree is ahead of, behind, or diverged from `origin/main`. Push first, or do not release. The rule is a precondition, checked before anything is built or numbered.

**Why it addresses the need.** It goes after the cause rather than the symptom. The version collision was downstream of the real condition: two trains holding different histories, neither able to see the other. In the observed case the builder's work sat two commits ahead of origin and unpublished while the loop released from its own view of the world — with a push-first rule, the builder pushes, the loop's next release sees that work, and there is one history for both trains to number against.

**How it differs from its siblings.** [[Derive the next version from the registry, never from the local file]] lets divergence continue and fixes only the number, so v0.19.0 can still contain work that v0.18.0's author never saw. This makes the divergence itself the error. It is the stricter rule and the one that produces a coherent release history rather than merely a non-colliding one.

**Where it fails, and it is a real cost.** It forbids something legitimate: releasing from a branch, cutting a hotfix from a detached state, or publishing a prerelease that deliberately should not be on `main`. It also does not actually prevent a race — two trains can both be perfectly in sync with `origin/main`, both read the same version, and both increment to the same number within the same minute. It narrows the window without closing it, and pairing it with its registry-checking sibling is probably what a human actually wants.

**And it inherits a live blocker.** Push and publish are both gated by the credential in [[Every run ends blocked on a credential only I hold]], so a strict push-first rule makes the credential holder a mandatory participant in every release. Given [[I need the tree's output to be actionable by compute alone, because my hours don't exist]], that is a genuine argument against this candidate and not a detail.

**Cost.** Very small: a `git rev-list --left-right --count` and a refusal.

⚠️ Unvalidated. Agent-ideated, 2026-08-02.

## History
- 2026-08-05 unlinked [[Count how many past releases a push-first rule would have blocked]] — moved under [[A push-first rule would have blocked few enough past releases to be adoptable]] — the belief this test measures now has a node of its own

## Proving this

[[Count how many past releases a push-first rule would have blocked]]

```
npx vitest run test/release/push-first-blocked-census.test.ts
```

Red today: the release path has no ahead/behind precondition to call, and nothing replays past releases against one. Green when the gate exists and the census can be taken.

**What a green run would not settle, and two of the three are the deciding questions.** The census answers only adoptability — how often the rule would have bitten. It does not touch this node's own stated cost, that the rule forbids legitimate branch releases, hotfixes from a detached state and deliberate prereleases; nor the admission that it narrows the collision window without closing it, since two trains in sync with `origin/main` can still read the same version in the same minute. And it says nothing about the live blocker recorded above: a strict push-first rule makes the holder of the credential in [[Every run ends blocked on a credential only I hold]] a mandatory participant in every release, which cuts directly against [[I need the tree's output to be actionable by compute alone, because my hours don't exist]]. That trade is a human's call and no exit code reaches it.
