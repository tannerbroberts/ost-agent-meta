---
type: Opportunity
status: unvalidated
source: 'INBOX:2026-07-24-opp-stakeholder-progress-view.md'
created: '2026-07-24'
evidence: assertion
---
#Opportunity #unvalidated #needs-customer-interview #evidence/assertion
[[Nothing points from my project to the vault that maps it]]
[[Nothing brings the tree's state to me, so staying current means going and reading it]]
[[The loop's highlights never reach me unless I go digging]]

**The need (customer's voice):** "I want to know where this thing stands — what it learned, what changed, what it's about to do — without opening a vault, learning a graph view, or reading Markdown files I didn't write."

**Why it matters:** The value of the tree is the compounding map, not the storage format. A filesystem-plus-Obsidian view is one optional lens; if it is the only lens, understanding progress costs more than the progress is worth, and stakeholders disengage — which also removes the humans who are supposed to run the tests and make the calls.

**Litmus test:** Many directions — a digest that arrives where stakeholders already are, a rendered web view, a diff-since-last-check summary, a spoken/narrated update, a single "what changed and why it matters" answer on demand. Passes.

**Provenance caveat:** Founder-stated. Which stakeholders, checking how often, and what decision they are trying to make are all unknown — that shape should come from interviews before anything is built.

Evidence: `INBOX:2026-07-24-opp-stakeholder-progress-view.md`

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 unlinked "Push digest where stakeholders already are" — re-parented under "Nothing brings the tree's state to me, so staying current means going and reading it" — this solution answers that need, not the categories beside it
- 2026-08-05 unlinked "Rendered tree view with diff since last visit" — re-parented under "Nothing brings the tree's state to me, so staying current means going and reading it" — this solution answers that need, not the categories beside it
- 2026-08-05 unlinked "Ask-anything conversational status" — re-parented under "Nothing brings the tree's state to me, so staying current means going and reading it" — this solution answers that need, not the categories beside it

## Issues
- 2026-08-11 INBOX:2026-08-11-observed-build-loop-reports-not-merged-on-merged-prs.md carries two defect shapes this sweep did not mint as nodes: (1) the ship step reports a local exit code as the fate of a PR without verifying the PR's remote state, so a succeeded merge was reported "NOT MERGED" twice; (2) the report truncated to nothing the very error text it existed to carry, making the defect undiagnosable from the report alone. Both read as instances of the report-versus-observation class the tree already holds (the evidence itself says "same defect class as the two already in the tree's memory"), but the closest sampled node ("A failed pass reports success, so my automation can't tell") claims the mirror direction. An attended pass with full tree sight should decide: corroborate existing nodes or mint one opportunity for false-failure reporting. The evidence item itself is discharged via the new node "The loop's highlights never reach me unless I go digging".
