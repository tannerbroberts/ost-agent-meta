---
type: Solution
status: unvalidated
source: 'INBOX:2026-07-24-opp-stakeholder-progress-view.md'
created: '2026-07-24'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A rendered tree orients a reader faster than the files do]]
[[A per-visit diff of the tree can be computed from the vault alone]]

A read-only rendered view of the tree — outcome at the root, opportunities sized and coloured by evidence strength, solutions and tests beneath — that highlights everything added or changed since that person last looked.

**How it differs from its siblings:** the only sibling that shows *shape*: where the map is thick, where it is thin, and how a branch ladders to the outcome. A digest describes changes; this shows structure.

**Trade-off:** it is still a place someone must choose to visit, and tree visualisations get unreadable as the opportunity space grows.

**Riskiest assumptions to test:** that structure is what stakeholders want, rather than a plain answer to "are we on track?" (desirability); that a tree of this size stays legible (usability).

Status: agent-originated candidate. Unvalidated.

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 unlinked "Five-minute orientation task on a static mock" — moved under "A rendered tree orients a reader faster than the files do" — the belief this test measures now has a node of its own

## Issues
- 2026-08-06 2026-08-06 In `solutionsMissingInstruments`, and an instrument would be a category error as this node stands. Its single Assumption child is "A rendered tree orients a reader faster than the files do" — a usability claim whose measurement is a reader, not an exit code. A spec file can assert that a renderer emits a particular shape; it cannot assert that the shape oriented anybody faster, and an instrument attached to this assumption would let a green test read as evidence the claim was settled. The sanctioned disposition is `ost_flag_humans_required`, which is withheld from the unattended surface, so this pass could not label it. For a human: either flag this test humans-required, or — if the intent is to build the renderer first — add a second, feasibility-shaped Assumption ("the tree can be rendered with per-visit diff from the vault alone") and instrument that one, leaving the reader claim to people. This node is a rendering candidate, so it is more likely than most of its queue-mates to be mistaken for feasibility work; that is why the note is here rather than only in the central census on "Filter the queue on shipped and count what is still unsatisfiable".

## Definition of done

The reader-shaped half of this solution stays with people, and four passes were right to refuse an instrument for it. What those passes recommended and none performed is now done: a second, feasibility-shaped belief has been separated out — "A per-visit diff of the tree can be computed from the vault alone" — and it carries a command.

"Render the tree across a recorded visit and require the second render to name exactly what changed"

    npx vitest run test/cli/tree-view-diff-since-last-visit.test.ts

Green means the diff is computable from the vault alone across a created node, a status transition and a merge. It does not mean anyone was oriented faster, and it must not be read that way — that claim is the assumption beside it and is measured by a reader, not an exit code.
