---
type: Solution
status: unvalidated
source: 'agent-ideation — from observed pass-shape decay in tetrix-ost 14:37→16:46'
created: '2026-07-25'
---
#Solution #ported-from-ost-agent-vault #evidence/assertion
[[Paper-classify the existing commit history as structure versus commentary]]

**The idea.** Stop trying to define "done" and instead detect *diminishing returns* from the shape of the agent's own output, then lengthen the interval between passes. Set-and-forget does not require the agent to finish. It requires the agent to stop spending money once it has stopped learning.

**The signal is already in the git history, and it is unambiguous.** Reading the tetrix vault's commits in order, one run decays visibly across two hours:

- 14:37–14:53 — `ost_create_node`, roughly thirty times. Opportunities, then solutions, then assumption tests. Structure being built.
- 16:44–16:45 — a handful of creates, then `ost_append_to_node` four times in a row: enriching nodes that already existed.
- 16:45–16:46 — `ost_annotate` on the root Outcome, twice, the second a 400-word essay.

Creates, then appends, then commentary on the root. The transition is legible from commit subjects alone — no semantic analysis, no judge model, no new instrumentation. Whatever else is true, **the last two commits of that run were not worth the same as the first thirty**, and the system had no way to notice.

**Why this is the honest solution to the termination problem.** The other two solutions here make `done: true` *reachable*. This one questions whether reaching it matters. A real product's evidence never stops arriving, so a tree that reports done is a tree that has stopped being fed, not a tree that is finished. The operator's actual question is never "is it done" — it is "is another pass worth the tokens." Answer that directly and the ledger's inability to clear stops being load-bearing.

**Sketch.** Classify each pass by what it wrote — new nodes, appends to existing nodes, annotations only. Consecutive commentary-only passes back the schedule off geometrically. Any new evidence in the inbox, or any human edit to the vault, resets it to the base interval. The operator gets a tree that costs real money while it is learning and almost nothing while it is waiting.

**What could go wrong.** A pass that produces only annotations is not necessarily low-value — the tetrix builder briefing was arguably the most useful artifact of the whole run, and it was the very last commentary-only commit. A crude classifier would have throttled immediately after the single most valuable thing the agent did. So the rule cannot be "annotations are worthless"; it has to be something closer to "annotations that repeat the previous pass's annotations are worthless," which is harder and probably needs the pass to compare against its own last output.

⚠️ Unvalidated. Proposed by an agent, from observed pass-shape decay in one run.

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
