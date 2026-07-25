---
type: Outcome
status: validated
source: 'config:outcome'
created: '2026-07-24'
evidence: assertion
---
#Outcome #evidence/assertion
[[I can't tell if anyone outside my own head wants this]]
[[I can't leave the process running unattended without worrying]]
[[Checking on progress means digging through files]]
[[Building crowds out the search for better evidence]]
[[What the agent learns doesn't accumulate over time]]
[[The goal I care about is too far from anything I can act on this week]]
[[Nothing kills a candidate, so every idea I have ever had is still alive]]
[[The candidate maps all look alike, so the route that would have worked is never among them]]
[[Don't want to buy a second AI credential just to try it]]
[[I have a tree full of unvalidated nodes and no idea which one to pick up]]
[[I opened the vault in Obsidian and the agent lost half the tree]]
[[The pass never says it is done, so I can't tell when to stop paying for compute]]
[[Trust an unmonitored agent enough to walk away]]
[[I don't know who this is for beyond myself]]
[[I can't say why anyone wouldn't just do this by hand with Claude and Obsidian]]
[[I don't know what unit of this anyone would pay for]]
[[No one outside my own network could discover this product exists]]
[[If the agent tends the tree for me, I may lose the understanding that tending it built]]
[[I want my usage to automatically feed into and make the OST-Agent better]]

Grow external returning operators: the number of non-founder operators who run a discovery pass on a real vault of their own and voluntarily return for another pass within 14 days, measured weekly. Until that number is above zero, the target opportunity is external demand evidence (I can't tell if anyone outside my own head wants this), and no node in this tree may climb the believability ladder on founder or model sources alone.

## History
- 2026-07-24 evidence: (none) → assertion — the mandate is a human decision, not a finding — the ladder floor

## Founder framing — 2026-07-24 (`assertion`; the mandate is unchanged)

Recorded from `INBOX:2026-07-24-founder-theory-purpose-levels-and-telemetry.md`, where the full text lives. This is positioning and rationale rather than an unmet need, so it produced no opportunity of its own; it is kept here because the opportunities distilled from that note rest on it. It has no evidentiary weight — it is one person's account of why the product should exist.

**The claimed position.** Two recursive-improvement loops already run: a global one (the AI field compounding on its own results) and a local one (an agent inside a context window finding evidence, drawing conclusions, and fixing its own problems within a single task). The claim is that this product sits at the seam between them — the global loop is too coarse to steer a specific goal, the in-context loop too small to persist past a session, and the OST is the artifact where information gathered at the local scale accumulates into something that compounds at the larger one.

**The claimed target capability.** Stated as a benchmark it does not yet have: *strategic decomposition of the task of getting the information needed to reliably build the thing requested.* Framed against tool-use benchmarks, where retrieval (grep-shaped) is easy to train because the reward is easy to cook up; this capability is harder precisely because the reward is the eventual movement of a metric, not the correctness of a lookup.

**The claimed neutrality.** All three levels — the global loop, the context window, and the OST — are goal-agnostic and pointable at an arbitrary human goal. The consequence the founder draws is that what the agent gathers must be *falsifiable and grounded* rather than asserted: "not just 'trust me bro'" but claims that could be shown wrong, tied to whether the core metric actually moved.

**What it cost the tree.** Four opportunities were distilled from the same note — raw usage telemetry (nested under the external-evidence branch), the altitude gap between a distant goal and an actionable metric, the absence of any mechanism that kills a candidate, and the risk that generated candidates are too alike for killing them to matter. All four are `assertion`-rung and inherit the provenance flag already recorded on this Outcome: the opportunity space below this node remains entirely founder-sourced.
- 2026-07-25 superseded mandate:
  > Ground the OST-Agent product in real EXTERNAL evidence: relentlessly increase the quantity and believability of validated, non-founder data about demand and usage, compress it into a trustworthy, ever-improving map from where the product is today to the metric we want to move, and keep that map compounding — so that goal + compute alone drive discovery and buildout, and stakeholders can trust the goal will not change and the process will not halt.
  > 
  > ## Issues
  > - 2026-07-24 Provenance gap across the whole tree (agent-flagged, 2026-07-24 pass). All 8 opportunities below this outcome were distilled from founder-authored inbox notes. None came from a story-based customer interview, and no node in this tree rests on non-founder evidence of any kind. By the tree's own rules this is the weakest possible provenance — the opportunity space is a set of hypotheses about needs, not a set of observed needs. The map should not be treated as believable until external evidence enters it; the branch "I can't tell if anyone outside my own head wants this" is the one that fixes this condition, and is the natural first target. A human should confirm the outcome and the opportunity set against real customer conversations before any building is funded off this map.

## Prioritization — row-by-row (2026-07-24, human-authorized hard-fix pass)

Torres: compare top-level rows qualitatively, pick ONE target, go deep. Verdict on the 13 rows against the retuned outcome (external returning operators):

- **TARGET → "I can't tell if anyone outside my own head wants this"** (status: in-discovery). The only row whose assumption tests create non-founder evidence; every other row's believability is blocked on it. Sized: affects the only current operator, every session, and gates all 148 unvalidated nodes.
- **Sequenced-after-demand:** "Trust an unmonitored agent enough to walk away" (41 nodes, ~28% of tree — adoption-stage hardening for operators who do not yet exist), "I can't leave the process running unattended without worrying", "Don't want to buy a second AI credential just to try it" (need reverse-engineered from a design decision). Hold until external returning operators > 0.
- **Dogfood lane (real, observed, but produces no external evidence):** "I opened the vault in Obsidian and the agent lost half the tree", "The pass never says it is done, so I can't tell when to stop paying for compute", "I have a tree full of unvalidated nodes and no idea which one to pick up", "Checking on progress means digging through files".
- **Founder-theory lane (evidence-debt-gated — no new siblings until a non-founder artifact cites the row):** "The goal I care about is too far from anything I can act on this week", "Nothing kills a candidate, so every idea I have ever had is still alive", "The candidate maps all look alike, so the route that would have worked is never among them", "Building crowds out the search for better evidence", "What the agent learns doesn't accumulate over time".

**Sequenced critical path inside the target row:** 1) Cold-offer test (run first — zero build, ~1 week, kill threshold pre-committed, every reply including the noes is this vault's first external evidence). 2) Two-week recruiting test for interview supply. 3) Pre-order probe (gated: without an audience source a null result cannot distinguish no-demand from no-traffic).

Source: INBOX:2026-07-24-external-review-five-dimension.md

## Issues
- 2026-07-25 Append-only violation on record (2026-07-24): merge 57c3745 rewrote 64 files' frontmatter and corrupted 5 source fields to a literal '>-'. Repaired same day under a distinguishable git author (commit a6d86cb) so human-driven repairs remain separable from agent passes. The port path's YAML serialization is filed as a product bug in INBOX:2026-07-24-external-review-five-dimension.md.

## Evidence dispositions — 2026-07-24 hard-fix pass

The 8 outstanding evidence items were dispositioned as follows. Because no acknowledge-with-reason affordance exists yet (see 'Let a pass mark evidence acknowledged, with a reason, without inventing an opportunity'), items that create no node will keep appearing as unmapped in ost_next_work — treat this ledger as the authoritative disposition, not the counter.

- `friction-two-loops-share-one-git-managed-vault` → MAPPED: new opportunity 'Two agents sharing my vault can trample each other' (observed rung).
- `friction-the-ost-vault-for-this-repo-is-not-discoverable` → MAPPED: new opportunity 'Nothing points from my project to the vault that maps it' (observed rung).
- `builder-evidence-debt-gate-verdict` → ACKNOWLEDGED: direct evidence for 'I have a tree full of unvalidated nodes...', appended there; no new need revealed.
- `friction-a-backgrounded-session-leaves-no-marker` → ACKNOWLEDGED: direct evidence for solution 'Resumable append-only process journal', appended there.
- `friction-a-new-node-level-requirement-is-unfixable` → ACKNOWLEDGED: evidence appended to 'Improving how the agent works means interrupting it'; re-confirmed live during this pass.
- `builder-transcript-harvester-shipped` → ACKNOWLEDGED: build+first-run note appended to solution 'Post-session transcript harvester'; feasibility evidence, not demand.
- `builder-loop-stopping-blocked-on-one-human-test` → ACKNOWLEDGED, no node: reports that `ost-agent result` (the human's half of the gate) now exists in the repo — but it is NOT in the shipped 0.1.3 CLI, so the human unblock path is still unreleased. Filed on the product bug list in INBOX:2026-07-24-external-review-five-dimension.md.
- `TRANSCRIPT:8fc8d6e3` → ACKNOWLEDGED, no node: one session, one tool_error friction event; too thin to ground anything alone; counted as first output of the harvester channel.

## Evidence dispositions — twenty-passes run (2026-07-25)

- `TRANSCRIPT:5e5c119d` (3 events: zsh glob errors ×2, vitest retry) and `TRANSCRIPT:8fc8d6e3` (1 tool_error) → ACKNOWLEDGED, no node: shell-harness micro-friction, not product friction; too thin to ground anything alone. Channel is working; signal this period is noise-level.
- `INBOX:…-friction-run-p2-p5-requires-an-api-credential…` → MAPPED: appended as first observed instance under 'Don't want to buy a second AI credential just to try it'.
- `INBOX:…-friction-a-pass-that-dies-on-a-driver-error…` → MAPPED: new opportunity 'A failed pass reports success, so my automation can't tell' (observed rung).
