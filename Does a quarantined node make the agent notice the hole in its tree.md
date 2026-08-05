---
type: AssumptionTest
status: unvalidated
source: agent-ideation — reproducible against this vault's current working tree
created: '2026-07-25'
evidence: assertion
instrument: npx vitest run test/ost/quarantine-unknown-node-type.test.ts
---
#AssumptionTest #ported-from-ost-agent-vault #evidence/assertion

**Assumption under test (feasibility).** That surfacing an unrecognized node as *present but unclassified* is enough for an agent reading only the tools to notice a branch is missing — and that it produces a clear diagnosis rather than the nine downstream symptoms it produces today.

**The fixture already exists and requires no setup.** This vault's working tree currently contains the failure: `Any steakholder can start the ost-agent npm package…` carries `type: Metric`, is absent from all 49 nodes returned by `ost_read_tree`, and its disappearance manifests as 4 orphan Opportunities, 3 orphan Solutions, and 1 dangling link from the Outcome. Do not fix the file. It is the test case.

**Pre-commit the threshold before starting.** After the change, `ost_read_tree` must return 50 nodes with exactly one flagged `unrecognized-type: Metric`, retaining its title, body, and all 8 outgoing links. `ost_next_work` must report the three affected Solutions as *quarantined-parent* rather than *orphan*, and the root's link must no longer be called dangling once the target is visible. And the count of hygiene issues attributable to this single edit must drop from 9 to 1 — because 9 symptoms for 1 cause is the actual defect, not a formatting complaint.

**The check that matters more than any count.** Hand a fresh agent nothing but the tool output and ask it what is wrong with the tree. Today, working from 9 scattered orphan warnings, it cannot recover the fact that a node exists on disk that it cannot see — it would report tree damage and proceed. If after the change it says "a node is present but unclassified, and these three solutions belong to it," the solution works. If it still cannot get there, quarantining is cosmetic and the reporting is what needs the work.

**Cost of being wrong is asymmetric and low.** If this assumption fails, the cost is a slightly better error message. If it holds, unattended passes stop silently operating on incomplete trees — which no amount of downstream quality work can compensate for, because every judge, every ranking, and every briefing inherits the hole.

⚠️ Proposed only — the agent does not run tests.

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 instrument: (none) → npx vitest run test/ost/quarantine-unknown-node-type.test.ts — The agent cannot notice a hole that leaves no trace, and today an unrecognised node type is dropped on read — which is the mechanism behind "I opened the vault in Obsidian and the agent lost half the tree". This asserts the quarantine: a node whose type is unknown is retained, excluded from counts and gates rather than miscounted, and surfaced by name in the sweep with the type that was not understood, so a vault edited by another tool loses nothing silently. Missing-spec red, not assertion red — nothing quarantines anything, so the command fails on a missing file; a builder should write it against the real vault reader so it goes red on a dropped node that today vanishes without a word. It does not settle whether the agent then ACTS on the hole, which is what the test asks and needs a person judging the pass output.
