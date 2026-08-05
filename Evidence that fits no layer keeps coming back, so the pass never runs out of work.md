---
type: Opportunity
status: unvalidated
source: >-
  tree-restructure:2026-08-05 — split from the bucket that held these solutions
  directly
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion
[[A Context node type for evidence that is true, useful, and not a customer need]]
[[Idle down when a pass produces commentary instead of structure]]
[[Let a pass mark evidence acknowledged, with a reason, without inventing an opportunity]]

Some of what arrives is true, useful, and not a customer need — and the tree has nowhere to put it. It is therefore never filed, so it is unmapped on the next pass and the one after, and a loop that is honestly finished cannot say so because the same items are still outstanding.

## The mechanism, established by test rather than inferred — 2026-08-05

Prior passes recorded *that* acknowledged evidence keeps returning. This pass established *why*, by trying the obvious workaround and watching it fail.

**Reuse is impossible, not merely discouraged.** The skill instructs a pass to "reuse an existing opportunity instead of duplicating." This pass tried it: it appended a fully-cited `## Evidence` section to "The same refusal is rediscovered every session, because nothing carries the lesson forward", naming three transcript ids in the body. `ost_next_work` was re-run immediately and reported the same 18 unmapped items, the three cited ones among them.

**An item is mapped when some node's frontmatter `source:` field equals the evidence id — nothing else counts.** Body citations are invisible to the sweep, however complete. And `source` is settable only at `ost_create_node`; no tool on any surface can add one to a node that already exists. So the only mechanical way to clear an item is to create a *new* node carrying that id, which for evidence that corroborates an existing need means minting a duplicate of a node the tree already has.

**That closes the loop this node describes into a genuine trap.** The pass is told to reuse rather than duplicate, and reuse has no representation. The 18 items have now been read, dispositioned and cited across at least four prior passes — the censuses on "What the agent struggles with every session disappears" cover most of them twice — and they will report unmapped on every future pass regardless.

**What this means for the solution beneath.** "Let a pass mark evidence acknowledged, with a reason, without inventing an opportunity" needs to write its acknowledgement somewhere the *sweep* reads, not somewhere a reader reads. A `## Disposition` section in a node body would not have worked; an entry in the ingest ledger, or an `acknowledges:` frontmatter field carrying a list of ids, would. That is a concrete constraint on the build, and it was not knowable before this test.

**This pass mapped none of the 18**, on the grounds that creating 18 opportunities to satisfy a counter would put 18 duplicate needs into a tree whose stated weakest point is that nothing in it is tested.

_Established by direct test on the 2026-08-05 unattended sweep — one append, one re-read, no change. Observed behaviour of the tool surface; grounds usability, not demand._
