---
type: Solution
source: 'agent-run:autonomous-loop-2026-08-06'
created: '2026-08-06'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

**The idea.** One append-only ledger of dispositions, written by a pass and read by every bucket. An entry names the item, the disposition, the reason, and the pass that wrote it — "this evidence corroborates a node the tree already has", "this solution ships", "this opportunity's solution space lives on its children". A bucket lists an item only if no live disposition covers it.

**Why the general form is worth its cost.** The three faces of this defect look like three bugs and are one absence: `ost_next_work` has no notion of "closed", so every bucket re-derives outstanding work from raw structure on every pass and each leaks differently. Both siblings fix one face by making the derivation smarter. Neither helps the next bucket to grow the same hole, and the evidence face cannot be fixed by a smarter derivation at all — "Evidence that fits no layer keeps coming back, so the pass never runs out of work" established by direct test that an item is mapped only when a node's frontmatter `source:` equals the id, that body citations are invisible to the sweep, and that no tool can add a `source:` to an existing node. There is nothing on disk for a cleverer predicate to read. Something has to be written.

**The constraint that node already discovered, which this design has to honour.** The acknowledgement must live somewhere the *sweep* reads, not somewhere a *reader* reads. A `## Disposition` section in a node body was tried and does not work. The ingest ledger, or a frontmatter field carrying ids, would.

**What it makes possible that neither sibling does.** A pass could finally be honestly done. Right now `done: true` is unreachable while 60 evidence items are permanently unmapped, so the loop's completion signal carries no information and the operator cannot use it to stop paying.

**Where it fails, and this is the serious one.** It hands the agent a way to make any work disappear by writing a sentence about it. Every other item on this list is removed by doing something checkable — shipping code, attaching a red instrument, creating a node. A disposition is removed by asserting. That is the same shape as the self-validation the whole tool surface is built to refuse, and it belongs to the party whose budget is spent by the work it would be dismissing. If this ships, the disposition write is the highest-risk write on the surface and probably wants the reserved-section treatment: legible, dated, attributed, and cheap for a human to audit in bulk.

**Cost.** A store, a write path, a read in every bucket, and a review surface so a human can see what a pass dismissed. Much the largest of the three.

⚠️ Unvalidated. Agent-ideated, and it is the candidate that most benefits the agent proposing it — discount accordingly.
