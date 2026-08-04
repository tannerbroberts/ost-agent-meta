---
type: AssumptionTest
source: 'WEB:arxiv.org/abs/2605.21997'
created: '2026-08-03'
evidence: assertion
threshold: >-
  At least 95% of tree-changing commits express as events with no residue, AND
  the projection of the full log is byte-identical to the current vault. Below
  90%, or any node the projection cannot reproduce, refutes it.
instrument: npx vitest run test/ost/event-log-projection.test.ts
---
#AssumptionTest #human-entered #feasibility #unvalidated #evidence/assertion

**The riskiest assumption is feasibility, not desirability.** The paradigm's value is uncontroversial if it works; what is unproven is that *this* tree can be expressed as an event log at all. If the vault's real history contains changes that do not decompose into a closed event vocabulary, the projection can never be authoritative and the whole architecture collapses to an audit log sitting next to a tree — which is [[Append-only audit trail the operator can replay]], already proposed, at a fraction of the cost.

**Why this is the cheapest disconfirmer.** It is retrospective and runs entirely against committed state — no build, no operator, no external party, no model call required for the mechanical part. The subject already exists: this vault carries a full commit history in which every write was made by the append-only MCP surface, which is the most favorable possible input. If it fails *here*, it fails everywhere.

**Method.**
1. Enumerate every tree-changing commit in `ost-agent-meta` (excluding `.ost-agent/usage/` sweeps and merge commits).
2. For each, attempt to express the diff as one or more events drawn from the vocabulary in step 1 of the parent node. Record any commit that leaves residue — a change no event describes.
3. Replay the resulting log through a projector and diff the output against the current vault, node by node.
4. Count the residue class separately from the mismatch class. They fail for different reasons and only one of them is fatal.

**Pre-committed bar:** as stated in `threshold`. Note the second clause is the strict one — a 99% expressible history that still projects to a tree differing from the real one is a refutation, not a pass, because near-determinism is not a contract anything can rest on.

**What a refuted result buys.** It kills an expensive rewrite before a line is written, and it names the specific changes that resist event-sourcing — which is itself the most useful thing this test can produce, more useful than a pass. Expect the hand-edit case (step 3 of the parent) to be where residue concentrates.

_Unvalidated — a human runs this and records the outcome with `ost-agent result`._

## History
- 2026-08-04 instrument: (none) → npx vitest run test/ost/event-log-projection.test.ts — The threshold is already written as two mechanical clauses — at least 95% of tree-changing commits express as events with no residue, AND the projection of the full log is byte-identical to the current vault — and the node's own method says it "runs entirely against committed state, no build, no operator, no external party". The spec walks every tree-changing commit, attempts to express each diff in the event vocabulary, counts residue, then replays the log through the projector and diffs node by node. It fails today because neither the event vocabulary nor the projector exists.
