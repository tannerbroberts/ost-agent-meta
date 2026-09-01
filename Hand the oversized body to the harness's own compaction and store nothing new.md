---
type: Solution
source: 'agent-ideation:2026-08-31-unattended-sweep'
created: '2026-09-01'
evidence: assertion
killIf: >-
  A compacted body is observed to drop or alter a claim the uncompacted body
  made, on any node a pass then acted on
killBy: '2026-12-15'
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[A compacted body preserves every claim a reader would have acted on in the full one]]

**Variation dimension: bought-vs-built. Position taken: the compression is adopted from outside as it is; only the trigger and the escape hatch are built here.**

Build no consolidation mechanism, no split, no append rule. Storage is untouched — the node stays one file and keeps growing. What changes is the read: a body past a byte budget is handed to the summarisation the surrounding platform already performs when a context grows too large, and `ost_read_tree` returns that rendering plus the file's true size and a flag to get the raw body. The thing being bought is a general-purpose distiller that is already paid for, already maintained by someone else, and already better at this than anything that would be written here.

**Why buy rather than build.** The sibling node above this one — "One distillation primitive behind every bounded surface, parameterized by goal and budget" — proposes building exactly such a distiller, and it is the most ambitious thing in this region of the tree. This candidate is the cheap test of whether that is necessary at all. If an off-the-shelf compactor gets a reader to the same decision, the primitive is a research project solving a problem that was already solved commercially, and the honest move is to find that out before starting it.

**Against the siblings.** Unlike the append rule, it needs nothing of any pass's restraint. Unlike the claim/commentary split, it touches no file layout, so no count, link, gate or reserved section can be routed into the half nothing reads — the single riskiest property of that candidate is absent here by construction.

**What it costs, plainly, and it is the worst cost of the three.** Everything a reader acts on has been through a paraphrase produced by something this project does not control and cannot pin. A compactor that drops the one sentence saying a claim was retracted produces a reader confidently acting on a withdrawn finding, and nothing in the output distinguishes that from a faithful rendering. This is directly at odds with the guarantee the product is built around — that a human's recorded finding cannot be altered by any tool — because a lossy read is an alteration everywhere it matters, even though the bytes on disk are untouched. Reserved sections would have to bypass compaction entirely and be served verbatim, which is a hard exception to enforce against a component nobody here maintains.

**What it also does not do.** It leaves the corpus growing. Storage cost, git diff size and the sheer accumulation are all unchanged; only the read is bounded, and the underlying accumulation is hidden rather than addressed — the same failure the parent opportunity's own sibling records about the 25-item display cap.

**What would make this the wrong pick.** If the fidelity check fails even once on a node someone acted on, this is unusable at any price, and the split candidate is the default. If it holds, it is available immediately and the other two are months of work for a problem already handled.

**Honest note on how this was ideated.** All three candidates under this opportunity were composed in one context by one author. The ruleset asks for one blind ideator per assigned dimension and this surface has no grant to run them, so discount their apparent distinctness accordingly.

Unvalidated. Agent-ideated 2026-08-31; a human to review.
