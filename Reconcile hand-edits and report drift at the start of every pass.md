---
type: Solution
status: unvalidated
evidence: assertion
source: agent-ideation — from the 2026-07-24 hand-edit incident in this vault
created: '2026-07-25'
---
#Solution #ported-from-ost-agent-vault #evidence/assertion
[[Can a pass tell a human edit from its own, using only git]]

**The idea.** Before doing any work, a pass diffs the vault against the last state it wrote, and reports what a human changed in between. Not to undo it — to *see* it, and to treat it as the highest-priority evidence in the vault.

**Why the first move is reporting, not repairing.** The hand-edit that broke this vault was not vandalism. It was a human expressing an opinion in the only language the substrate gave them: renaming the umbrella opportunity to the full goal sentence, and retyping it `Metric`. Read as a diff, that is an operator saying *this node is my goal, and it is a metric, and your schema has no word for that.* Read as corruption to be repaired, it is noise to be silently reverted — and the product would have thrown away its single most direct piece of user feedback to make a hygiene counter go down. **Human edits are not drift from the agent's truth; they are the closest thing this product has to an interview.**

**The mechanical part is nearly free.** The vault is already a git repository and every tool-driven change is already a commit with a machine-written subject (`mcp: ost_create_node — created …`). Any commit that does not look like that, or any dirty working tree at pass start, is a human edit. That is a `git log` call, not a design project. The 0-byte file and the dangling link in this vault are both visible from `git status` alone.

**What the pass should then do.** Surface the diff prominently — a builder briefing and a drift report are the same genre and probably the same node. Re-attach orphans the history can justify: `ost_link_nodes` can legitimately re-parent an Opportunity to the Outcome. Refuse the repairs it cannot justify: three orphan Solutions in this vault belong to the human's now-invisible node, and picking a different parent to clear the warning would be inventing structure. And treat repeated edits to the same node as a strong signal that the node is wrong, not that the human is careless.

**The failure mode to design against.** An agent that reports drift every pass, forever, for edits the human made deliberately and does not intend to revert. Drift needs to be acknowledgeable, or it becomes another permanent false alarm — the exact fate of the unmappable evidence item under the sibling opportunity.

⚠️ Unvalidated. Proposed by an agent, from a single observed incident.

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
