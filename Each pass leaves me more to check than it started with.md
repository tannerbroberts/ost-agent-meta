---
type: Opportunity
source: 'USAGE:2026-08-03'
created: '2026-08-05'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion
[[A shipped solution leaves the instruments queue, because built behaviour cannot carry a red-now command]]

I pay for a pass hoping it will close questions. The tool-invocation trace says it opens them instead, and it does so at a rate nothing downstream can absorb.

On 2026-08-03 the vault recorded 312 tool invocations across six sessions. **237 of them — 76% — were `ost_create_node`.** The next-largest was `ost_next_work` at 39, which is the pass re-asking what is outstanding. Everything that consolidates rather than adds — `ost_append_to_node` at 15, `ost_annotate` at 6 — together came to under 7% of the day.

Set that against what the tree has to show for it. It now holds 920 nodes. **Zero assumption tests have ever been run.** Across every bucket the rollup reports, the built fraction sits between 0% and 14% and the believability floor is `assertion` — the rung meaning nobody outside the building has said anything. The production rate and the verification rate are not merely mismatched; one of them is zero.

The need underneath this is not "make the tree smaller". It is that **a pass should cost me less to review than it saves me**, and right now the arithmetic runs the other way: every pass hands back more unchecked claims than a human could read, so the reviewing debt compounds while the evidence does not. An operator watching that happen has no reason to run a second pass, which is the failure mode that matters — not an untidy tree, but a loop that is rational to stop paying for.

Contrast with its siblings so nobody merges these by mistake. "Nothing kills a candidate, so every idea I have ever had is still alive" is about the absence of a pruning mechanism — things never leave. This is about the *rate at which they arrive*, which would still outstrip verification even if pruning worked. And "I have a tree full of unvalidated nodes and no idea which one to pick up" is about choosing among what exists; this is about how much gets added before the choosing ever happens.

## Evidence class

Machine-recorded trace of tool invocations, with no narrator — this is the loop observing itself. Declared at the `assertion` rung rather than `observed` on purpose: the `USAGE:` channel records what the *agent* did, and a measurement of the agent's own behavior is not a measurement of anybody's demand. It establishes that the imbalance is real; it says nothing about whether an operator minds. A prior pass had exactly this call refused for claiming `observed` on a `USAGE:` source, which is recorded in the same day's trace as its one failed call.

## What would move this

A count, not an opinion: the ratio of nodes added per pass to nodes that reach a recorded result or a cleared gate. Today the denominator is zero, so the ratio is undefined — and an undefined ratio is itself the finding.
