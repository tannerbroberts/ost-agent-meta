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

## Definition of done — and it is not a command

"A person reads ten compacted bodies and marks every claim the full body made that the rendering dropped"

No command: this one is humans-required on purpose. The bar is **zero dropped negations, retractions or stated limits across all ten**. The failure this test exists to catch produces no error and no flag — a compacted body reads fluent and confident whether or not a retraction was dropped — so there is nothing for an exit code to observe. Absence is only visible to a reader who knows what was there.

Cheapest first move: the two nodes named on the parent opportunity, at 30,395 and 8,875 characters, are already identified and both dense with qualifications. Running those two will very likely settle it, in which case the other eight are never needed.

The test title is quoted rather than wikilinked on purpose: its one backlink belongs to its parent assumption.

## 2026-09-02 — the "hard exception nobody here maintains" already has machinery here, and it is half of what this candidate needs

Four lines, and it is a correction to this node's own cost paragraph rather than another census.

**The claim being qualified.** This node states its worst cost as unmanageable in kind: reserved sections "would have to bypass compaction entirely and be served verbatim, which is a hard exception to enforce against a component nobody here maintains." That is written as though the enforcement would have to be invented alongside the bought compactor.

**What is actually in the repository.** Read first-party this pass: `src/compression/registry.ts` declares every bounded surface in this product with four fields — the `decision` it serves, the `reads` that decision depends on, whether it `drops` silently or names what it dropped, and whether its `proof` is a declaration or a behavioral drive. `test/compression/fidelity-contract.test.ts` enforces that registry in three parts: a **census** that greps every cap constant out of `src/` and fails the build if one is unclaimed, phantom or double-owned; two **ratchet lists** (`SILENT_SURFACES`, `DECLARATION_ONLY_SURFACES`) pinned by name outside the registry so a new silent clip or a new unproven contract can only be added by a reviewer editing the list; and a **fidelity** part that runs the real production code over fixtures for the ten surfaces marked behavioral, `tree read` among them. Its own header states the purpose in the words this node needs: the caps "were each cut in after an unbounded read did damage, and what the squeeze must PRESERVE lived only in per-module comments — so a new cap could ship silent, and an old one could rot, without anything going red."

**What that does to this candidate, in both directions.** It *lowers* the build cost: a bought compactor would enter as one more registered surface, and it could not ship without declaring what its squeeze preserves — the census refuses an unregistered cap, and the silent-clip ratchet makes "this one drops things without saying so" a reviewed decision instead of a drift. So the exception is not unprecedented here; it is the shape this repository already has a jig for. It does *not* touch the risk this node is actually built around. The registry's guarantees are structural — a contract is declared, a fixture's known content survives — and the failure named here is semantic: a fluent paraphrase that silently omits a retraction. That is why the machinery being present does not make this node's humans-required Definition of done redundant, and it stays unchanged.

**Limits.** The registry's contents are read off one spec file plus its imports, not off `src/compression/registry.ts` itself, which this pass did not open; the surface count and the `tree read` drive are taken from the test's own lists. The fidelity file was served truncated, so the `tree read` drive's assertions were not read — only its presence in `DRIVEN_SURFACES`. Whether a reserved section is inside any declared `reads` contract today was **not** checked and should not be inferred from this note. Nothing was executed, no rung moved, no instrument set, no status changed.

_Method: `ost_read_repo` reads of `test/` and `test/compression/fidelity-contract.test.ts`. Observed structure of this product — it grounds feasibility, not desirability, and is not evidence that anyone wants this._
