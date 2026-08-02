---
type: Solution
source: 'agent:ideation-2026-08-02'
created: '2026-08-02'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

**Candidate (unvalidated, agent-ideated — one of three deliberately different mechanisms under this opportunity).**

**The mechanism.** The vault holds a pinned, committed copy of the agent it runs — the bundled server, the ruleset, the generated skill — and upgrading is `git pull` in the vault, an operation the operator already performs and already trusts. Propagation stops depending on a package registry, an auth token, or anyone's publish permission; it depends on the same repository the tree already lives in and the same append-only history that records everything else.

**What it is good at.** It routes around the constraint this vault has recorded more often than any other: publishing needs a credential no unattended pass may hold, while committing to the vault is something every pass already does. It also makes version skew *diffable* rather than inferred — the version an instance ran on any past date is recoverable from the same git history the pass notes live in, which no other candidate here gives. And it fits the stated positioning (local, operator-owned vaults) without adding a network dependency at pass start.

**Where it fails, stated plainly.** Every vault becomes a fork. Two vaults that pulled on different days run different agents against the same rules, and a fix shipped to one is invisible to the other until someone remembers — which is the opportunity restated one level down rather than solved. It also asks the operator to do something: `git pull` is a human action, and this tree's mandate is explicitly about work compute can carry alone. Worst case it converts an invisible skew into a visible one that still nobody closes, and it inflates every vault with a copy of the product, so a repository meant to hold evidence starts holding a build artifact.

**Compare against:** [[Resolve the newest published version at pass start and refuse to run silently on a stale one]] keeps the registry and inherits its credential; this one abandons the registry and inherits fork drift instead. [[A push channel the operator subscribes to, applied at the next safe checkpoint]] keeps a single source of truth but adds a channel pointing inward at the operator's machine.

**Assumption it rests on:** that an operator would accept the agent living inside their own vault rather than installed beside it. Tested by [[Would an operator accept the agent living inside the vault it maintains]].
