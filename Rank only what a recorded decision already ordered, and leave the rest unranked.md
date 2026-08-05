---
type: Solution
source: 'agent-ideated:2026-08-02-unattended-sweep-priority-order'
created: '2026-08-02'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Enough of the tree is already ordered by a recorded human decision to rank from]]

**The mechanism:** the agent never authors a priority. It reads the ordering already recorded in the vault — the root's Prioritization section, the evidence-debt gates written into node bodies, lane labels, WIP holds, founder decisions — and renders each row's "why" as a citation of the human decision that put it there. Rows no recorded decision reaches are published as **unranked, and named**, rather than being assigned a position the agent invented.

**Why this shape.** It is the only one of the three candidates that structurally cannot manufacture a priority, which matters because the agent proposes and never disposes. It also turns the tree's most expensive recurring cost into an artifact: the root ledger records four consecutive passes re-deriving the same held-row judgement from prose, each pass paying to reconstruct what an earlier one already decided. This candidate reads that judgement once and shows it.

**Chief risk, stated plainly:** coverage. On a fresh tree almost nothing has a recorded decision, so this mechanism ranks nearly nothing and the operator gets a long unranked tail — which is honest but not yet useful, and is the exact opposite failure to the ledger candidate's fluent-reason-for-everything. It also inherits every contradiction in the record rather than resolving it: the distribution row, where a founder decision names it the critical path while the node's own gate says do not expand it, would render as a row citing two decisions that point opposite ways. That is arguably the correct output, but it is a report of a deadlock rather than a priority.

**Cost shape:** cheap to build and cheap per pass, but its usefulness is entirely a function of how much governance a vault has already written down — it gets better with age instead of working on day one.

## Definition of done

"Count how much of the tree a recorded decision could actually order"

```
npx vitest run test/ost/recorded-decision-ordering.test.ts
```

Green means the ranking covers exactly what a recorded decision supports and the remainder is explicitly unranked rather than silently ordered. The count is the point: if recorded decisions can order only a small fraction of the tree, this candidate is honest but nearly empty, and that is worth knowing before building it. It does not settle whether an unranked remainder is usable by anyone.

## History
- 2026-08-05 unlinked "Count how much of the tree a recorded decision could actually order" — moved under "Enough of the tree is already ordered by a recorded human decision to rank from" — the belief this test measures now has a node of its own
