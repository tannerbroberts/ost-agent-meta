---
type: Opportunity
status: unvalidated
source: 'observation:this-vault working tree + ost_next_work output, 2026-07-24'
created: '2026-07-25'
---
#Opportunity #ported-from-ost-agent-vault
[[Detect renames from link topology and repair the edge]]
[[Quarantine unknown node types instead of dropping them]]
[[Reconcile hand-edits and report drift at the start of every pass]]

**Customer need (operator's perspective):** "You told me it's just Markdown in Obsidian. So I renamed a node and fixed its type. I didn't get a warning, and eight nodes quietly stopped existing as far as the agent is concerned."

## Evidence — this vault, right now, uncommitted

At 14:25–14:27 on 2026-07-24 a human edited this vault by hand — the exact interaction the product invites by choosing Obsidian Markdown as its substrate. Two changes: the umbrella opportunity `Trust an unmonitored agent enough to walk away` was renamed to the full goal sentence `Any steakholder can start the ost-agent npm package, pour compute and a goal into it, and trust it to efficiently map out the path to accomplishing the goal`, and its frontmatter `type:` was changed from `Opportunity` to `Metric`.

Both edits are reasonable. Neither is destructive in intent. The result:

- `ost_read_tree` returns 49 nodes and **the renamed node is not among them** — an unrecognized `type:` value makes a node invisible rather than flagged, so its 8 outgoing links vanish with it.
- The old file remains on disk at 0 bytes, so the root Outcome now carries a dangling link.
- `ost_next_work` reports 9 hygiene issues: 4 orphan Opportunities and 3 orphan Solutions that were the invisible node's children, plus the dangling link.
- Silent. No pass failed. No warning was emitted. The next unattended pass would have run happily against a tree missing its largest branch.

**The agent cannot repair most of this.** `ost_link_nodes` can re-attach the orphan Opportunities to the Outcome, because they are defensibly facets of it. The three orphan Solutions cannot be honestly re-parented — their real parent is the invisible node, and inventing a different one would misrepresent the human's structure to make a hygiene counter go down. The append-only surface is right to forbid the repair; it is wrong to offer no way to *report* it as anything other than one more annotation nobody reads.

## Why this matters more than its size suggests

Every other risk in this tree is about the agent doing something bad. This is the inverse: the *human* does something ordinary and the agent silently degrades. It attacks set-and-forget from the side nobody is guarding — and it is the only failure here that scales with how much the operator actually engages with their own vault. The more they trust it enough to open it, the more they break it.

There is also a substantive signal buried in the edit itself, distinct from the mechanical failure and worth a human's attention: the operator reached for a node type called `Metric`, which the schema does not have. Both this instance and the tetrix instance have now bumped into the same shortage of node types from opposite directions — one wanting somewhere to put context, one wanting somewhere to put a metric.

**Litmus (more than one way?):** Yes — reconcile and report drift at the start of every pass; treat unknown `type:` values as present-but-quarantined rather than absent; detect renames by content/link topology and repair the edge; warn on write instead of at next read; give the agent a scoped repair affordance for edges it can justify from history.

_Provenance: direct observation of this vault's working tree and `ost_next_work` output, 2026-07-24. Unvalidated — one incident, one operator._

## History
- 2026-07-24 provenance repaired: frontmatter source was corrupted to ">-" by the 57c3745 vault merge; restored from the body's provenance footnote (human-authorized repair).
