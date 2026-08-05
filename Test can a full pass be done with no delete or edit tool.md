---
type: AssumptionTest
status: unvalidated
source: 'INBOX:2026-07-22-safety-requirement.md'
created: '2026-07-25'
evidence: assertion
---
#AssumptionTest #ported-from-ost-agent-vault #evidence/assertion

**Risk category: Feasibility.** Riskiest assumption: the entire maintenance workflow can be accomplished with only create / append / annotate / set-status — no delete or edit is ever genuinely required.

**Proposed test (small, fast):** Run several representative passes (including hygiene and correction scenarios) using only the append-only tools; log any task that could not be completed without a missing verb.

**Pre-committed success threshold:** zero workflows blocked by the absence of delete/edit; every correction expressible as an append/annotate/status change.

_Proposal only — a human reviews the outcome. Unvalidated._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule

## Issues
- 2026-08-05 Premise appears overtaken by events, and this node has not caught up. Its riskiest assumption is stated as "the entire maintenance workflow can be accomplished with only create / append / annotate / set-status — no delete or edit is ever genuinely required", with a pre-committed threshold of "zero workflows blocked by the absence of delete/edit". The tool surface has since grown `ost_edit_node`, `ost_detach_nodes` and `ost_merge_nodes`, and the merge tool's own rationale is that annotating a duplicate "leaves two nodes and adds a third claim, which is how a tree accumulates overlap it cannot resolve" — i.e. a workflow that WAS blocked by the absence of a destructive verb, which is what this threshold asked about. On its face the assumption was refuted and the answer was acted on before the test was recorded. Three things keep this from being a verdict, which is why it is annotated rather than resolved: the agent cannot record a result at all; the shipping of a verb is not the same as a counted census of blocked workflows, which is what the threshold actually specified; and it is possible the maintainer considers edit/merge a convenience rather than a necessity, in which case the assumption stands and the new verbs are unrelated. What would settle it is cheap — a human replaying representative correction and hygiene passes against a create/append/annotate/set-status-only surface and counting what cannot be completed, then recording the result with `ost-agent result`. Until then this node reads as an open question whose answer is sitting in the product's own changelog. Deliberately not instrumented by the 2026-08-05 pass: a spec written now would be built against verbs that already exist and could not go red honestly.
