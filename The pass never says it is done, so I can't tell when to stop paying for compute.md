---
type: Opportunity
status: unvalidated
source: >-
  observation:.ost-agent/state/mapped.json behaviour in this vault +
  RUNTIME:tetrix-ost@2328e61
created: '2026-07-25'
evidence: assertion
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
