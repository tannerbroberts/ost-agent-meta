---
type: Opportunity
status: unvalidated
source: 'INBOX:2026-07-24-opp-idempotent-runtime.md'
created: '2026-07-24'
evidence: assertion
---
#Opportunity #unvalidated #needs-customer-interview #evidence/assertion
[[Two agents sharing my vault can trample each other]]
[[A failed pass reports success, so my automation can't tell]]
[[A run that dies while I am away stays dead, and nothing says where it stopped]]
[[The unattended run is scoped for tools nobody granted it, and it finds out one denial at a time]]
[[A run's own leftovers break the next run's setup, so the loop fails before it starts]]
[[An interrupted run leaves no trustworthy account of what it completed]]
[[A change I ship can only reach the agent by stopping it first]]
[[The session tries to write a file before it has read it this run, and the guard fails the turn instead of reading first]]
[[Merging a build branch conflicts on the compiled dist file from a concurrent firing, stalling the run]]
[[A backgrounded session leaves no marker of what it finished versus abandoned]]
[[The Monitor tool refuses the exact commands an unattended run needs to check on its own background work]]
[[The build loop re-selects a solution I already marked deferred and re-derives the same disproven result]]
[[A probe I write outside the repo can't import the repo's modules, and only running it says so]]
[[A command stops to ask a yes no question and the unattended run has nobody to answer it]]
[[My bounded wait gives up before the job it is watching finishes, so the run stalls on work that was still healthy]]
[[The wait stops at its own default while the call I made still had time left]]

**The need (customer's voice):** "If I hand a goal and some compute to an autonomous agent and walk away, I need to come back to a system that is still running and still pointed at the same goal — and if I stop it or it crashes mid-step, I need to be able to start it again without wondering what got half-written."

**Why it matters:** The whole promise is that goal + compute drive discovery without supervision. Any doubt about halting, drift, partial writes, or stuck locks collapses that promise back into babysitting, which costs more attention than doing discovery by hand.

**Litmus test:** Several plausible directions — crash-safe append-only writes, resumable checkpoints, a supervisor that restarts work, a visible liveness signal, a goal-immutability guarantee. Passes.

**Provenance caveat:** Founder-stated and unvalidated. It is a trust need, so the real test is whether stakeholders actually walk away — observed behavior, not stated intent.

Evidence: `INBOX:2026-07-24-opp-idempotent-runtime.md`

## What separates this bucket from "Trust an unmonitored agent enough to walk away"

**This bucket is about the run continuing to work. The sibling is about the run's conduct and output being believable.** Stated here because the 2026-07-25 flag below correctly said the titles do not carry the boundary, and a reader still has to guess which child lives where.

The boundary, in one line each:

- **Here:** did the machinery keep running, and can it be restarted without damage? Crashes, locks, half-writes, stale leftovers, denied tool grants, a merge conflict on `dist`, a loop re-selecting work already deferred. The failure mode is *the run stopped, stalled, or corrupted itself.*
- **There:** can I believe what it did while nobody was watching, and could it have done something I would not sanction? Grading its own homework, unproven work dressed as proven, leaking a connected system of record, a destructive irreversible action, no audit trail of the time I was away. The failure mode is *the run worked perfectly and I still cannot trust the result.*

**Torres's test, applied 2026-08-22 rather than assumed.** A solution addressing one and not the other exists in both directions, which is what makes these real siblings rather than one need wearing two titles: "Resumable append-only process journal" answers continuity and does nothing for honesty; an independent judge that grounds the agent's claims answers honesty and does nothing for continuity. Neither is a candidate for the other's branch. **So the merge reading of the flag below was tested this pass and fails** — the remaining live question is naming, not merging.

**Why a naming decision is still owed.** The distinction is real but neither title says it: both read as "unattended agent, anxiety about it." A reader routing a new child still has to read this section to place it. Renaming is a human's call and cannot be done from this surface at all (a title is the filename), so it stays open below.

## Issues
- 2026-07-25 Near-synonym top-level sibling of 'Trust an unmonitored agent enough to walk away' — the children happen to partition (safety/honesty vs runtime continuity) but the titles do not carry the boundary; a reader cannot predict which child lives where. Merge-or-rename candidate for human decision (2026-07-24 review).
  - 2026-08-22 Narrowed, not cleared, by the unattended sweep. The merge half is answered: Torres's test was applied against both nodes' actual children and they pass as distinct siblings (see the section above), so this should not be merged. The rename half stands and is the only decision left — an agent surface cannot change a title, and both titles still fail to carry the boundary the children respect. Prose now states the boundary explicitly so the flag stops costing a reader a guess while the naming question waits.

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 unlinked "Resumable append-only process journal" — re-parented under "A run that dies while I am away stays dead, and nothing says where it stopped" — this solution answers that need, not the categories beside it
- 2026-08-05 unlinked "Supervisor heartbeat with automatic restart" — re-parented under "A run that dies while I am away stays dead, and nothing says where it stopped" — this solution answers that need, not the categories beside it
- 2026-08-05 unlinked "Immutable goal contract" — re-parented under "A run that dies while I am away stays dead, and nothing says where it stopped" — this solution answers that need, not the categories beside it
- 2026-08-07 link "I can't tell what a half-finished run actually finished" repointed to "An interrupted run leaves no trustworthy account of what it completed" — that node was merged away
- 2026-08-09 link "Improving how the agent works means interrupting it" repointed to "A change I ship can only reach the agent by stopping it first" — that node was merged away
- 2026-08-22 body edited — The 2026-07-25 flag asked a merge-or-rename question that has sat undecided for four weeks while the node's prose said nothing about what separates it from its near-synonym sibling — so every reader and every sweep re-derived the boundary from the children. Adding the differentia the flag says is missing, and recording that the merge half of the question was tested against Torres's test this pass and fails. No prior claim removed; the original flag is preserved verbatim with a dated sub-bullet.
