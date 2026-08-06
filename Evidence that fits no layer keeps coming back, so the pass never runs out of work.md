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

## The backlog this trap holds has grown from 18 to 62 — 2026-08-06

The mechanism above was established on 2026-08-05 against 18 stranded items. One day later the unattended sweep reports **62**, and the growth is not neglect — it is the trap operating as described, plus a channel that produces new items faster than any pass could mint nodes for them. The transcript adapter captured 2 more during this pass's own opening `ost_ingest_inbox` call.

**This pass classified all 62 rather than mapping them, and the classification is the finding.** Every friction class in the corpus already has an opportunity in this tree:

| Friction class | Occurrences | Already filed as |
|---|---|---|
| Read-before-write refusal | ~45 across 18 sessions | "Every precondition is discovered by violating it, so a pass pays a turn per rule it did not know" |
| Ungranted MCP tool (`ost_flag_humans_required` ×25, `ost_check` ×22, `ost_status` ×14, `ost_debt` ×4) | ~65 across 27 sessions | "The unattended run is scoped for tools nobody granted it, and it finds out one denial at a time" |
| Product-repo read denied for permissions | ~18 across 16 sessions | "The agent's repo sight fails mid-pass, because nothing checked the product path before it was needed" |
| Stale or unmatched edit target | 7 | "The file changed after I read it, and the failed edit is how I find out" |
| Response refused for size | 2 | "Every response that can be refused for size states its size first" |
| Malformed call body | 1 | "A malformed call lands before anything checks it, and only reading back the file says so" |

Not one item revealed a need the tree does not hold. So the honest disposition for all 62 is *acknowledged, corroborates an existing node* — which is exactly the disposition this opportunity exists because nothing can express.

**What is new here, beyond a larger number.** The 2026-08-05 test showed reuse cannot be recorded. This census shows what that costs at scale: the 62 items are not a queue of unexamined signal, they are 62 receipts for six needs, and a channel that will keep issuing them. The remedy under this node — an `acknowledges:` list the sweep reads — would clear all 62 in six calls if it existed, one per class. Without it the only mechanical clearing move is to mint 62 duplicate opportunities, which would grow this tree's opportunity layer by half again with nodes that restate six claims.

**One consequence for the believability rollup, worth a human's attention.** These six opportunities are the most heavily corroborated needs in the vault — dozens of mechanically captured observations each — and most of them read `rests on assertion`. That is partly a bookkeeping artefact of the same defect: `observed` requires provenance that is itself a recording, `source:` is settable only at creation, and these nodes were created citing inbox notes or agent ideation. The corroboration exists and cannot be attached. A reader taking the rollup's floor rung at face value will under-rate exactly the needs this product has the most evidence for.

_Census taken 2026-08-06 by direct count over `.ost-agent/evidence/TRANSCRIPT_*.md`. Counts are occurrences of each refusal string, not sessions; session counts are given where they differ. Re-checkable by anyone with the vault._

## Measured — 63 items, and citing one in a body does not retire it (unattended sweep, 2026-08-06)

This pass ingested 2 new transcript records and found **63 unmapped evidence items**, all from the transcript channel. Five were read in full. Their content is, without exception, needs this tree already holds:

- permission denials for tools the pass was told to use — held by "The unattended run is scoped for tools nobody granted it, and it finds out one denial at a time"
- denied reads of the product repository — held by "The agent's repo sight fails mid-pass, because nothing checked the product path before it was needed"
- `Edit` refusing with "File has not been read yet" and "File has been modified since read" — held by "The file changed after I read it, and the failed edit is how I find out"
- byte-identical re-calls of `ost_ingest_inbox` and `ost_next_work` inside one session — held by "A third of my calls go on re-asking what is outstanding"
- a tool invoked whose schema was never fetched — held by "Every precondition is discovered by violating it, so a pass pays a turn per rule it did not know"

**The mechanical finding, which is the part worth keeping.** An item is retired from the unmapped queue only by a node whose **`source:` frontmatter** carries its exact id. A citation in a node *body* does nothing. This is checkable rather than inferred: `TRANSCRIPT:516fdfb8-bab1-41a4-b1e5-92fde97bd90d` is cited by name in the corroboration table on "The same refusal is rediscovered every session, because nothing carries the lesson forward", and in four separate corroboration sections on "My loop spends its time waiting for a check it cannot subscribe to" — and it is still on this pass's unmapped list.

**So the queue has exactly two exits, and both are wrong.** Either create a node per item — 63 opportunities restating needs the tree already carries, which is the duplication debt the ruleset forbids — or leave them outstanding forever, in which case `done: true` is unreachable and every future pass re-reads the same records to reach the same conclusion. Corroborating an existing node, which is the *correct* handling and what several passes have done at length, is the one action that changes nothing about the queue.

**What would settle it:** whether corroboration counts as mapping. If a body citation retired an item, the honest handling and the queue-clearing handling would be the same act, and this node's whole complaint dissolves. The tree already holds a proposed mechanism for this — the test "Blind-review a pass's acknowledge-or-map calls on the seven stranded items", instrumented at `test/ost/evidence-acknowledge.test.ts` — and it remains unbuilt, which is why the count went from seven stranded items to sixty-three.

_Source: `ost_next_work` output of 2026-08-06; records `022e473f`, `2a4bcf6e`, `49d6b2d3`, `c41b49d0` and `e6e8542c` read in full; the `516fdfb8` citation checked directly against both node files. Observed behaviour of this product's own sweep. Corroboration only; the node's rung is unchanged._
