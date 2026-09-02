---
type: Opportunity
status: unvalidated
source: >-
  observation:.ost-agent/state/mapped.json behaviour in this vault +
  RUNTIME:tetrix-ost@2328e61
created: '2026-07-25'
evidence: assertion
authorship: machine
---
#Opportunity #ported-from-ost-agent-vault #evidence/assertion
[[Work my own governance has already gated still shows as outstanding every pass]]
[[Nothing tells an honest loop to stop, so it either idles or invents work]]
[[My loop spends its time waiting for a check it cannot subscribe to]]
[[Evidence that fits no layer keeps coming back, so the pass never runs out of work]]
[[Work a previous pass settled comes back on the next list, so I pay to re-decide it]]
[[Work I already finished keeps coming back in the queue, so the pass can never say it is done]]
[[Near-identical evidence can only be discharged by giving each copy its own node]]
[[Most of my backlog has never been read once, because every firing is shown the same alphabetical first 25]]
[[The biggest queue on my report is one the surface reading it to me has no tool to clear]]
[[Work I already decided needs a person comes back every pass as work I failed to do]]

**Customer need (operator's perspective):** "Set-it-and-forget-it means I need to know when forgetting it is still buying me something. Right now it never finishes, and I can't tell the difference between working and idling."

## Evidence — the same failure, reached independently by two instances

**This vault.** An autonomous pass distilled all 7 inbox items into sourced Opportunities, gave every opportunity ≥3 Solutions and every Solution ≥1 AssumptionTest — and `ost_next_work` still reported all 7 items as `unmappedEvidence`. The mapped set lives in `.ost-agent/state/mapped.json`, written only by the batch `P2_map` process runner; `ost_create_node` never touches it and no MCP tool exposes a way to mark evidence mapped. The agent correctly refused to hand-edit the state file (that would break the tools-only trust boundary) and annotated the root instead.

**The tetrix vault, four hours later, with no knowledge of the above.** The same wall, reached from the other direction. Its annotation:

> "Because the mapped-evidence ledger tracks nodes carrying an evidence `source`, and no node carries this one, `ost_next_work` will continue to report it as unmapped on every future pass and the tree will never report `done: true` on this item alone."

That instance hit it for a *principled* reason worth preserving: one evidence item recorded existing de-risked capability, containing no unmet customer need. Distilling an Opportunity from it would have meant inventing a need the evidence did not support. So the agent deliberately declined, appended the content to the Outcome as discovery context, and accepted a permanent outstanding flag. It was right to decline. The tool surface punished it for being right.

**Two distinct defects sit underneath this, and they should not be conflated:**

1. *Mechanical:* nothing a session-driven pass can do updates the mapped ledger, so `done: true` is unreachable by construction.
2. *Semantic:* not all evidence maps to an opportunity. Context and constraints are legitimate discovery products with nowhere to live. Both instances independently invented the same workaround — dumping prose into the root Outcome body — because the schema has no home for "true, useful, and not a customer need."

**Consequence for the outcome.** A loop that cannot terminate cannot be economized. The operator is asked to pour compute in with no signal for when the marginal pass stops paying for itself — and the observed shape of a late pass is not new nodes but longer essays annotated onto the root. That is the point where compute should idle down, and there is nothing to detect it.

**Litmus (more than one way?):** Yes — expose a mark-mapped affordance; let a pass declare evidence "acknowledged, not mapped" with a reason; add a Context/Constraint node type so non-need evidence has a home; detect diminishing returns from the pass's own output and idle down; separate "structurally complete" from "nothing left worth doing."

_Provenance: `.ost-agent/state/mapped.json` behaviour in this vault (confirmed in prior session, see root annotation), plus the tetrix instance's root annotation at commit `2328e61`. Unvalidated._

## History
- 2026-07-24 provenance repaired: frontmatter source was corrupted to ">-" by the 57c3745 vault merge; restored from the body's provenance footnote (human-authorized repair).
- 2026-07-24 evidence: (none) → observed — retro-labeled: recorded-as-it-happened incident in this vault / tetrix-ost with commit-level provenance
- 2026-08-01 evidence: observed → assertion — demoted by the fifteenth pass — B3's rung-unearned guard (v0.23.0-line) shipped after this node was authored; its source is not a TRANSCRIPT: recording, so 'observed' was unearned. Demotion only, per rungs.ts's own remedy.
- 2026-08-05 unlinked "A Context node type for evidence that is true, useful, and not a customer need" — re-parented under "Evidence that fits no layer keeps coming back, so the pass never runs out of work" — this solution answers that need, not the categories beside it
- 2026-08-05 unlinked "Idle down when a pass produces commentary instead of structure" — re-parented under "Evidence that fits no layer keeps coming back, so the pass never runs out of work" — this solution answers that need, not the categories beside it
- 2026-08-05 unlinked "Let a pass mark evidence acknowledged, with a reason, without inventing an opportunity" — re-parented under "Evidence that fits no layer keeps coming back, so the pass never runs out of work" — this solution answers that need, not the categories beside it

## Two more mechanisms, observed live (2026-07-25, twenty-passes run)

1. **Done-ness is not stable across versions.** `INBOX:2026-07-25-friction-upgrading-the-cli-silently-reopened-18-mapped-ev.md`: same vault, same instant — 0.1.3's source-scan says 9 unmapped, the HEAD build's ledger (a file no pass here ever wrote) says 27. An upgrade re-opened 18 items of settled history without touching the tree.
2. **The counter cannot read governance.** `INBOX:2026-07-25-friction-ost-next-work-demands-solutions-under-7-opportun.md`: 7 opportunities carry explicit evidence-debt/prioritization gates, but underservedOpportunities re-demands solutions under them every pass, forever. A governed pass and a quota-filling pass see the same number; done:true is unreachable by design either way.

Both are observed-rung, machine-recorded. Between them and the original mapped-ledger dead-end, this opportunity now has three independent mechanisms.

## Evidence: three mechanisms observed (mapped 2026-07-25)

- `INBOX:2026-07-25-friction-ost-next-work-demands-solutions-under-7-opportun.md` — the underserved counter cannot read governance gates, so 7 gated opportunities are re-demanded every pass, forever; done:true is unreachable by design for a governed agent.
- `INBOX:2026-07-25-friction-passes-8-through-13-produced-zero-structure-whil.md` — six consecutive passes reported identical outstanding work and produced zero structure; a governed agent idles, an ungoverned one would confabulate, and nothing in the loop says stop.
- `INBOX:2026-07-25-friction-upgrading-the-cli-silently-reopened-18-mapped-ev.md` — done-ness is not stable across versions: 0.1.3 said 9 unmapped, HEAD said 27, because mapped-ness switched to a ledger no pass had ever written.

Together: "done" is undefined against governance, against idleness, and against upgrades — three independent ways the meter never stops.

## A fourth mechanism, measured this pass (2026-08-02)

The three mechanisms above predicted this would keep happening. It did, and the specific shape has changed again, which is itself the finding.

**Measured, same instant, same vault.** `.ost-agent/state/mapped.json` holds 33 dispositioned ids. `ost_next_work` reported 32 unmapped. The two sets overlap heavily — `INBOX:2026-07-24-builder-evidence-debt-gate-verdict.md`, `INBOX:2026-07-24-market-scan-ai-ost-competitors.md`, `INBOX:2026-07-25-friction-upgrading-the-cli-silently-reopened-18-mapped-ev.md` and roughly a dozen more sit in the ledger *and* in the unmapped list simultaneously.

**What that means.** The 2026-07-25 filing recorded done-ness moving *from* a source-scan *to* a ledger. It has now moved back, or diverged: the ledger written by the batch `P2_map` runner is no longer what `ost_next_work` consults. The current rule is observably `source`-field-scan — an item counts as mapped only when some node carries it in frontmatter `source:`, one id per node. So this is not the same defect recurring; it is the *third distinct accounting rule* this vault has been measured against, and the ledger those earlier passes were told to write is now inert.

**Why appending does not help.** Several of these items are mapped in substance and have been for weeks — this node's own "three mechanisms" section cites three of them by id, in prose, with analysis. That work is real and is not counted, because prose in a body is not a `source:` field. An evidence item that corroborates an *existing* opportunity therefore has no way to be recorded as handled: `ost_create_node` sets `source` only at creation, and there is no affordance to add a second source to a node that already exists. The only counter-clearing move available is to create a new node per evidence item, which is precisely the duplication the tree's rules forbid.

**Consequence, stated plainly for whoever reads this next.** The unmapped counter cannot reach zero by honest work on this vault's current contents. A pass that respects the no-duplicates rule will report the same backlog forever; a pass that clears the counter will have manufactured near-duplicate opportunities to do it. Both prior candidates under this node — "Let a pass mark evidence acknowledged, with a reason, without inventing an opportunity" and "A Context node type for evidence that is true, useful, and not a customer need" — address the semantic half. Neither addresses this mechanical half: **many-to-one evidence, where one opportunity is corroborated by many items.** That gap is now the binding one and a human should decide it; this pass has not invented a node to close it.

## Measured during the unattended pass of 2026-08-06

This need has a mechanism, and this pass walked into it with numbers attached.

The pass opened by ingesting: 11 new items from the transcript channel, joining 15 already unmapped, for 26. It then did the mapping work — read all 26 records in full, distilled three new opportunities from them. Before re-checking, it ingested again, as the loop requires. That second ingest captured **18 more**, and the outstanding count went from 26 to **40**. The pass had mapped for an hour and finished with 54% more unmapped evidence than it started with.

Nothing malfunctioned. The transcript channel harvests this vault's own unattended firings, and unattended firings are what this vault does. Every pass generates the session record that the next pass must map. So `unmappedEvidence` is not a backlog that a diligent pass drains — it is a treadmill whose speed is set by how often the loop runs, and a pass instructed to loop "until done" over a bucket fed by its own execution cannot terminate on that bucket by working harder.

Three consequences worth separating, because they want different fixes:

The first is that "done" is the wrong shape for this bucket. A pass can honestly finish having mapped every record *it was shown at the start*, and that is a completable job; "no unmapped evidence exists" is not.

The second is that the counter overstates the work. Of the 18 records captured in the second ingest, every one was another unattended firing recording the same three needs already distilled that morning — permission denials, a write refused for a read-first precondition, a string parsed as syntax. Mapping them would have produced duplicate opportunities, so the honest action was to leave 15 of them unmapped, which is indistinguishable in the count from not having done the work.

The third is the cost question this node is actually about. Compute spent re-reading self-generated friction that corroborates a need already on the tree buys corroboration, and corroboration has sharply diminishing returns: the sixth recording of `ost_flag_humans_required` being denied changes no decision the first five did not already support.

Provenance: this pass, 2026-08-06, first-party. Not an ingested record — citing an id for a session that has not ended is the fault flagged on four other nodes in this vault this morning.

## A fifth mechanism, on a different bucket: `solutionsMissingInstruments` has a floor it cannot go below (unattended firing, 2026-08-28)

The four mechanisms above all concern `unmappedEvidence`. This one concerns the instruments bucket, and it matters separately because the remedy is different and because that bucket is the one the firing prompt weights most heavily.

**What was measured.** `ost_next_work` reported 64 solutions "whose tests are prose only", capped to 25 shown. This pass read 8 of the 25 in full. **Eight of eight were legitimately un-instrumentable, and seven already carried a prior pass's written reasoning saying so.** They fall into four kinds, none of which a spec can reach:

- *The belief is about a person.* "A highlight criteria note the founder edits…" and "A human-edited manifest of loop-prescribed call sequences…" both rest on whether the founder maintains a recurring-input artifact. "Axioms elicited at the moment a derivation needs them…" rests on whether asks arrive rarely enough to be answered. No exit code settles any of them.
- *The artifact is not in this repository.* The Monitor candidates and "Auto-read a file before the first write or edit…" are about the harness's own tool surface. No spec in `test/` can reach it — a point "Maintain a running per-item task list…" already records verbatim.
- *A sibling's test already owns the mechanical half.* "Ship the helper with its own runtime…" says so explicitly and names the sibling's harvester.
- *An instrument would be a false red.* "Append-only tool surface with no delete or shell tool" is the sharp case: a spec asserting "no delete tool exists" would go red today and a builder could act on it — removing `ost_merge_nodes`, a feature added deliberately. That node records seven passes declining on exactly this reasoning.

**Why the counter cannot drop.** The tool that would move the human-only ones off the list is `ost_flag_humans_required`, and it is withheld from the unattended surface by design. Four of the eight nodes say so in their own prose and name the human's remedy, `ost-agent lane --set`. So a well-behaved unattended pass can neither instrument these nor relabel them: the only two moves that would clear the count are both off this surface. The number is a floor, not a queue.

**Why this is not mechanism #2 restated.** The 2026-07-25 finding was that `underservedOpportunities` re-demands solutions under governance-gated opportunities. Same shape — a counter that cannot read why work is deliberately not being done — but a different bucket with a different fix: that one needs the counter to read a gate recorded *on the node*, this one needs it to read a lane recorded *on the test beneath the solution*, which already exists as a field. `assumptionWork.needsHumans` reported 464 entries this pass, so the lane data is there and populated; the instruments bucket simply does not consult it. That makes this the cheapest of the five to close.

**The honest reading of the number, for whoever consumes the report.** "64 solutions cannot reach a builder" invites the conclusion that 64 pieces of work are waiting. On this sample the truer statement is that some smaller number are waiting and the rest are correctly parked — and nothing in the response distinguishes them, so each firing re-reads nodes to rediscover which is which. This pass spent most of its budget doing exactly that, which is the compute cost this opportunity exists to name.

**What this does not establish.** Eight of sixty-four is a sample, not a census, and it is drawn only from the 25 the cap made visible — the same alphabetical-head problem "Most of my backlog has never been read once…" records beside this node. The 39 hidden entries were not examined and may contain genuine work. A census would settle the share and none was run.

_First-party to this firing: the `ost_next_work` response and eight `ost_read_tree` node reads. Observed behaviour of this product's own surface; it grounds usability, not desirability. No test was run and no result is recorded._

## 2026-09-01 — the compute cost this node names, measured by a machine instead of asserted by a pass

Kept short. One number, from a channel that has never been cited on this node before.

**Why this is not another section of the same.** Every cost claim on this node is a pass's account of its own budget — the 2026-08-28 section closes "This pass spent most of its budget doing exactly that, which is the compute cost this opportunity exists to name," and offers no figure. `USAGE:2026-09-01`, captured at this firing's ingest, is the append-only tool-invocation trace rolled up mechanically: its own header states "Computed, not composed: no agent narrated, selected, or summarized these numbers." It is the first measurement of this node's subject that no agent authored.

**The day, across 21 sessions and 491 MCP calls (489 ok, 2 failed, p50 68ms).**

| | calls | share |
|---|---|---|
| Reads — `ost_read_tree` 210, `ost_read_repo` 98, `ost_next_work` 93 | **401** | 81.7% |
| Ingest — `ost_ingest_inbox` | 42 | 8.6% |
| Structural writes — `append_to_node` 23, `create_node` 21, `link_nodes` 1, `annotate` 1, `edit_node` 1, `set_instrument` 1 | **48** | 9.8% |

**What that says, and it is the ratio rather than the total.** Twenty-one firings spent four calls reading for every one that changed the tree. `ost_read_tree` alone — re-reading node bodies, which is how a pass rediscovers which parked items are parked on purpose — is 210 of 491, more than reads of the product repository and sweeps combined. Averaged out, a firing costs roughly 23 calls and leaves 2.3 structural writes behind. The 2026-08-28 section infers exactly this shape from one pass's felt experience; the trace puts a denominator under it for a whole day of firings.

**The sharpest single figure is on instruments, the bucket the firing prompt weights most heavily.** Across all 21 sessions, `ost_set_instrument` succeeded **once**, and both of the day's only two failed calls were the other two attempts — one `ost_create_node` and one `ost_set_instrument`, each refused for the same reason, an instrument written with a `-t "…"` filter hitting the shell-punctuation guard. So instrument authoring ran at 1 of 3 attempts for the day, and the two losses were the documented grammar limit rather than anything new. That limit is already established first-party on "My tests carry thresholds nobody ever fixed, so nothing can come out a failure", which reads `src/knowledge/instruments.ts` in full; this adds only that the cost is still being paid, by a second channel, on a day nobody had flagged.

**What this does not establish.** One day, and a day of unattended firings specifically — it is not a rate for attended work. The trace's Surface table reads `mcp: 491`, so harness-side calls (`Read`, `Glob`, `Edit`) are outside it: this is the read/write ratio of the MCP surface, not of everything a pass does, and the true read share is higher rather than lower. It also says nothing about whether the reads were *wasteful* — a read that stops a pass duplicating a node is worth making, and this node's own argument is that many of them are re-derivation rather than that all of them are. Separating those two is the open question, and no artifact on disk currently distinguishes them.

**Not mapped, and that is this node's own first defect.** `USAGE:2026-09-01` corroborates an opportunity that already exists, so there is no honest node to create for it and no affordance to add a second `source:` to this one. It will therefore be reported as unmapped evidence on every future pass — the many-to-one gap the 2026-08-02 section names as the binding one, demonstrated once more by the very record that measures its cost.

_Source: `USAGE:2026-09-01`, read in full via `ost_next_work({evidence})`. Machine-recorded trace of this product's own agent — it grounds usability and the agent-tool loop, not external demand. Nothing executed, no rung moved, no instrument set, no status changed._
