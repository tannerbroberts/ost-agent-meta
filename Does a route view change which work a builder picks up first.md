---
type: AssumptionTest
status: unvalidated
source: 'INBOX:2026-07-24-founder-theory-purpose-levels-and-telemetry.md'
created: '2026-07-25'
evidence: assertion
---
#AssumptionTest #unvalidated #usability #evidence/assertion

**Assumption under test:** That seeing a path (rather than a tree) changes behaviour — if builders open the same node either way, the view is decoration.

**Design:** Give six builders the same tree, three with the route view and three without, and record which node each opens first and why. **Pre-committed threshold:** the route-view group converges on a first pick (at least two of three agree) while the control group does not. Same picks either way means the tree was already legible and this is not the constraint.

*Proposed only. A human runs this.*

**Provenance caveat:** Founder-stated in a single spoken rant, not sourced from a story-based customer interview. Believability rests on the floor rung (`assertion`). This is a hypothesis about a need, not an observed need; a human should confirm or discard it against real customer conversations before anything is built off it.

Evidence: `INBOX:2026-07-24-founder-theory-purpose-levels-and-telemetry.md`

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule

## Issues
- 2026-08-05 2026-08-05 unattended sweep — triaged as humans-required, lane not settable from this surface. Its parent solution "Route view showing the shortest credible path from here to goal-achieved" sits in `solutionsMissingInstruments`, and no instrument belongs here: the design names outside people as the sample — "Give six builders the same tree, three with the route view and three without, and record which node each opens first and why" — and the node states "Proposed only. A human runs this." A command cannot produce six builders' first picks. `ost_flag_humans_required` was refused on this sweep (not granted), so a human should set the lane with `ost-agent lane --set`. Recorded so this is not re-triaged next pass.
