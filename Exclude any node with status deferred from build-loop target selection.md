---
type: Solution
source: 'agent-ideated:2026-08-19-unattended-sweep'
created: '2026-08-19'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[The build loop's target-selection query has no status filter, or an incomplete one, letting deferred nodes back into the candidate pool]]

Add `status !== 'deferred'` as a hard filter in whatever query the build loop runs to pick its next target, alongside whatever "has an instrument, cleared its permit" filter it already applies. Cheapest possible fix if the loop is simply not checking status at all — a one-line predicate change.

**What would make this the wrong pick.** If the loop already filters on status and the real bug is that it's reading a stale snapshot of the node (a caching issue), this fix does nothing: the stale copy would still report `status: unvalidated` or whatever it was cached as before the human deferred it. Worth checking which is true before building this.

⚠️ Unvalidated. Proposed by an unattended pass reasoning from three observed build-loop reports; no repo sight available this pass to confirm which failure mode is actually present.

## The failure mode is confirmed, and it is the incomplete-filter one (repo read, 2026-08-21 unattended sweep)

This node was written without repo sight and named two candidate failure modes, saying which one is true should be checked before building. It has been checked. `src/eval/buildable.ts` was read in full this pass.

**It is the incomplete filter, not a stale snapshot.** Two functions in that file answer different questions and only one consults status:

| Function | What reads it | Filters `deferred`? |
|---|---|---|
| `solutionsMissingInstruments` | the discovery queue | **yes** — `if (n.status === "deferred") continue;` |
| `buildableSolutions` | the build loop's target pool | **no status check at all** |

`buildableSolutions` iterates every `Solution` and calls `permitFrom`, which checks only that a test exists, declares an instrument, and has been observed red and not green. Neither function in that path looks at `status`. So a solution a human abandoned, whose test still carries a red observation, leaves discovery's queue and stays in the builder's.

**The disconfirmer this node named is ruled out.** The body says the one-line predicate is the wrong fix "if the loop already filters on status and the real bug is that it's reading a stale snapshot." There is no snapshot: `buildableSolutions(tree)` takes the tree as an argument and reads `n.status` off live nodes, and nothing on the path caches. The cheap predicate fix is the right shape after all.

**Worth noting for whoever builds it:** the fix is not one line but two decisions. `solutionsMissingInstruments` already carries a written rationale for trusting the bare `deferred` field (unlike `shipped`, which requires a trusted promotion recorded in `## History`), and the same reasoning transfers — but the natural place to put the check is `permitFrom`, which would also change what `buildPermit` answers for a single named solution, not just what the pool returns. Those are different blast radii and the choice belongs to a person.

**This is an observation of the code, not a result.** Nothing here clears a gate. It does, however, answer from source the question standing with the operator as "Ask someone with the build loop's target-selection source open whether it filters candidates on status" — the answer is that the target-selection path does not.

_First-party read of this product's own source via `ost_read_repo`. Grounds feasibility only; rung stays at the `assertion` floor._

## Definition of done

"buildableSolutions drops a deferred solution that still carries a red instrument"

```
npx vitest run test/eval/buildable-status-filter.test.ts
```

Two solutions in the fixture, each carrying a test observed red — one `deferred`, one `unvalidated`. `buildableSolutions` must return exactly one entry, the unvalidated one. Today it returns two.

Named in plain quoted text rather than as a wikilink: the test is linked exactly once, by the Assumption above it.
