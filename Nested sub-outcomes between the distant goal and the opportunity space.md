---
type: Solution
status: unvalidated
source: 'INBOX:2026-07-24-founder-theory-purpose-levels-and-telemetry.md'
created: '2026-07-25'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[Two practitioners place the same opportunity under the same sub-outcome]]
[[The invasive part is the metric field, not the nesting, because the Opportunity layer already nests recursively]]

Allow a layer of movable sub-outcomes under the root: the root holds the distant goal, each sub-outcome holds a metric that can visibly move inside a working cycle, and opportunities attach to a sub-outcome rather than directly to the goal. Altitude becomes explicit structure instead of a judgement each reader re-makes.

**Contrast with siblings:** The most invasive option — it changes the schema and every existing node's ladder-up path. "Contribution estimates" gets much of the same clarity with no structural change; "Route view" leaves the tree alone entirely and changes only what is rendered.

**Provenance caveat:** Founder-stated in a single spoken rant, not sourced from a story-based customer interview. Believability rests on the floor rung (`assertion`). This is a hypothesis about a need, not an observed need; a human should confirm or discard it against real customer conversations before anything is built off it.

Evidence: `INBOX:2026-07-24-founder-theory-purpose-levels-and-telemetry.md`

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 unlinked "Do two practitioners place the same opportunity under the same sub-outcome" — moved under "Two practitioners place the same opportunity under the same sub-outcome" — the belief this test measures now has a node of its own

## Issues
- 2026-08-05 Possible duplicate, not merged — flagged for a human because this pass is not confident the two are the same claim. "Keep the goal I actually want as the outcome, and hang the affordable one beneath it as a milestone" proposes what looks like the same structural change: a named layer between the root Outcome and the opportunity space, so a distant goal can stay at the root while something reachable sits under it. This node calls that layer a sub-outcome and that one calls it a milestone. On 2026-08-05 the two were given instruments asserting near-identical mechanisms — `test/ost/milestone-under-outcome.test.ts` for the other — and if they are one claim, the tree is about to grow two builds of one layer under two names. What would settle it: whether nesting is meant to be recursive. A sub-outcome that can itself parent sub-outcomes is a genuine new layer in the hierarchy; a milestone is a single flat marker between the root and the buckets. If the answer is that both mean one intermediate level, these should be merged and the surviving prose should say which word the product will use. That is a naming decision with build consequences, which makes it a human's, not this pass's.

## Definition of done

"A sub-outcome metric survives a serialize round-trip, and no existing opportunity is re-parented to get one"

`npx vitest run test/ost/sub-outcome-layer.test.ts`

**What the spec has to assert (from the test's own threshold).** Three things: a node carrying a sub-outcome metric keeps the metric string through one `serialize` then `deserialize`; an Opportunity nested under another Opportunity is accepted with no change to the hierarchy rules; no existing opportunity needs re-parenting for the layer to exist.

**State of the command on 2026-11-12.** The spec file does not exist in the product repository (probed this firing). A run today files as `no-spec`, which is not a red about this question. The builder's first deliverable is the spec failing on the round-trip assertion.

**What a green does not settle.** Feasibility and cost only. Whether the layer is legible sits with "Two practitioners place the same opportunity under the same sub-outcome", which is a person's to answer. The sub-outcome versus milestone duplicate in this node's Issues section is still open and still a human's naming decision; building this before it is answered risks two builds of one layer.

The test title is quoted, not linked: its one backlink belongs to its parent assumption. Added by the 2026-11-12 unattended sweep; nothing was executed.
