---
type: Solution
source: 'INBOX:2026-07-24-friction-a-backgrounded-session-leaves-no-marker-of-where.md'
created: '2026-08-18'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[Sessions update the task list as they go, not only at a clean end a backgrounded session never reaches]]
[[A task list a prior session left behind saves more than it costs, and won't get acted on when stale or wrong]]

Have each session maintain a structured task list (done / in-progress / not-started) in a known location, updated as it works rather than only at the end. If backgrounded or interrupted, whatever it last marked in-progress is exactly the boundary the next pass needs, without inferring it from raw transcript events.

**Compared to the alternatives.** Gives the next pass structured, per-item status rather than a single last-action timestamp — more useful when a session was mid-way through a multi-step plan. Depends on the agent itself keeping the list current, so a session that dies mid-step without ever marking that step in-progress leaves the same gap this opportunity describes, just narrower.

## Issues
- 2026-08-17 Assumption surfaced ("Sessions update the task list as they go, not only at a clean end a backgrounded session never reaches") but its test is not created: this is a usability/behavioral question best answered by observing real sessions rather than a mechanical spec. Left prose-only for an attended pass or human to design.
- 2026-08-22 2026-08-22 unattended sweep, repo sight held: re-checked for an unstated mechanical belief and found none worth writing. Both assumptions here are genuinely behavioral — whether a model keeps its list current as it works, and whether a later session trusts a stranger's list — and the artefact they are about (the harness's own task list) is not in this repository, so no spec in `test/` can reach it. This confirms rather than clears the 2026-08-17 note above. Deliberately left prose-only; not a skipped step.

## 2026-11-01 — the previous firing's reads came back as this firing's first evidence record, and this firing had already repeated two of them

Short note. It adds one first-party observation.

**What happened.** This firing's `ost_ingest_inbox` captured one new record, `TRANSCRIPT:3bb26330-b83b-4f63-82e3-11530468d66a`: 7 retries from the previous unattended firing. Its calls included `ost_read_tree` on "The agent can decompose my goal but cannot acquire and test its own guesses about how to reach it", "Name the engine's published dialect in the tool description and build no validator of our own", "Route the humans-required solution into the ask queue instead of dropping it from the instrument queue" and this node. Before this firing read that record, it had already read the first three of those bodies in full (about 56,000 characters in total) and reached the same verdicts they already carry: the ideation hold stands, and neither solution can honestly take an instrument from this surface.

**Why it belongs here.** That is exactly the cost this candidate is meant to remove. The tree already held the verdicts as prose on each node, but nothing told the next pass *before* it opened the bodies that the verdicts were settled and unchanged. The record that would have told it showed up as unmapped evidence, after the reads were done.

**Limits.** One pair of consecutive firings. I am reading "retry" as a call this firing had made before, not checking it call by call (see the sibling concern that a parallel call can be filed as a retry). Nothing was executed, and no instrument, lane, rung or status changed. `ost_check` is withheld on this surface, so this write is unverified by design.
