---
type: Opportunity
status: unvalidated
evidence: observed
source: 'observation:.ost-agent/state/mapped.json behaviour in this vault + RUNTIME:tetrix-ost@2328e61'
created: '2026-07-25'
---
#Opportunity #ported-from-ost-agent-vault #evidence/observed
[[A Context node type for evidence that is true, useful, and not a customer need]]
[[Idle down when a pass produces commentary instead of structure]]
[[Let a pass mark evidence acknowledged, with a reason, without inventing an opportunity]]

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

## Two more mechanisms, observed live (2026-07-25, twenty-passes run)

1. **Done-ness is not stable across versions.** `INBOX:2026-07-25-friction-upgrading-the-cli-silently-reopened-18-mapped-ev.md`: same vault, same instant — 0.1.3's source-scan says 9 unmapped, the HEAD build's ledger (a file no pass here ever wrote) says 27. An upgrade re-opened 18 items of settled history without touching the tree.
2. **The counter cannot read governance.** `INBOX:2026-07-25-friction-ost-next-work-demands-solutions-under-7-opportun.md`: 7 opportunities carry explicit evidence-debt/prioritization gates, but underservedOpportunities re-demands solutions under them every pass, forever. A governed pass and a quota-filling pass see the same number; done:true is unreachable by design either way.

Both are observed-rung, machine-recorded. Between them and the original mapped-ledger dead-end, this opportunity now has three independent mechanisms.

## Evidence: three mechanisms observed (mapped 2026-07-25)

- `INBOX:2026-07-25-friction-ost-next-work-demands-solutions-under-7-opportun.md` — the underserved counter cannot read governance gates, so 7 gated opportunities are re-demanded every pass, forever; done:true is unreachable by design for a governed agent.
- `INBOX:2026-07-25-friction-passes-8-through-13-produced-zero-structure-whil.md` — six consecutive passes reported identical outstanding work and produced zero structure; a governed agent idles, an ungoverned one would confabulate, and nothing in the loop says stop.
- `INBOX:2026-07-25-friction-upgrading-the-cli-silently-reopened-18-mapped-ev.md` — done-ness is not stable across versions: 0.1.3 said 9 unmapped, HEAD said 27, because mapped-ness switched to a ledger no pass had ever written.

Together: "done" is undefined against governance, against idleness, and against upgrades — three independent ways the meter never stops.
