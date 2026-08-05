---
type: Assumption
status: unvalidated
source: >-
  tree-restructure:2026-08-05 — the belief this solution's test was already
  measuring
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Test can a full pass be done with no delete or edit tool]]

Safety here comes from the capability being absent. That is only viable if the work is actually doable without it — if a pass regularly needs to remove or rewrite something, the missing tools become a wall rather than a guarantee.

## Issues
- 2026-08-05 **Superseded by the product — flagged 2026-08-05, for a human to resolve.** This assumption, and the solution above it ("Append-only tool surface with no delete or shell tool"), describe a design the product has since moved away from. The tool surface an unattended pass is handed today includes `ost_edit_node` (replaces a node's prose), `ost_detach_nodes` (removes an edge) and `ost_merge_nodes` (folds a duplicate away and **deletes its file**). The governing instruction now states it plainly: *"The vault is no longer append-only, and what replaced it is narrower than 'anything goes'."*

So the belief has effectively been answered, but sideways — not by the test beneath it ("Test can a full pass be done with no delete or edit tool") returning a verdict, but by the product deciding it did not want the property. What replaced append-only is not the absence of the guarantee; it is a narrower one: three reserved sections (`## Results`, `## Uncovered`, `## Instrument Log`) that no tool in either direction can author or destroy, plus `## History` still append-only, plus git behind everything.

Two reasons this was annotated rather than acted on. Recording a verdict is a human's `ost-agent result`, and a pass that quietly marked a branch dead because the world moved would be selecting outcomes on its own authority. And no instrument was attached: the requirement is that a command fail today and pass when the solution is built, but this solution will not be built — an honest command here would be red permanently, which measures nothing.

**Suggested for a human:** `deferred` on this assumption and on the solution above it, with a note pointing at the reserved-section rule as the guarantee that actually survived. If the narrower property is worth keeping as a live claim, it wants a new assumption stated in its own terms rather than this one edited to mean something it never said.
