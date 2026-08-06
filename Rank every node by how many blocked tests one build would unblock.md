---
type: Solution
status: unvalidated
source: agent-ideation — generalized from tetrix-ost commit 2328e61
created: '2026-07-25'
evidence: assertion
---
#Solution #ported-from-ost-agent-vault #evidence/assertion
[[Unblock count changes which node an operator actually picks]]
[[Unblock counts are near-uniform across a real tree, so ranking by them orders nothing]]

**The idea.** Compute, for each candidate build, how many *other* assumption tests become readable if it ships — and surface that ratio as the tree's primary ordering. Not importance, not effort, not confidence. Unblocking count.

**Why this specific shape, and not generic scoring.** It is the ranking a running instance derived on its own, unprompted, when it had no ranking affordance. The tetrix agent found that instrumenting the anonymous funnel makes four otherwise-unreadable tests readable — four tests spanning an entire top-level opportunity — and wrote: *"One instrument unblocks all four. This is the clearest case in the tree of a small build with leverage over a large branch."* It reached that by reading four test bodies and noticing they all pre-commit to thresholds today's telemetry cannot measure. That is exactly the kind of cross-node reasoning a tool can do reliably and a human skims past.

**Why not the obvious alternatives.** Impact scoring asks the agent to guess at value, which is the one thing it has no evidence for and every incentive to confabulate. Effort scoring rewards whatever is cheap. Unblocking-leverage is different in kind: it is a *structural* property of the tree, computable from the nodes themselves, and it does not require the agent to have an opinion about the business. That makes it hard to game and easy to audit — the operator can check the claim by opening the four tests and seeing whether they really are blind.

**Sketch of the build.** An assumption test declares what it needs in order to be readable (a measurement, a decision, a shipped capability). Another node declares what it provides. Leverage is then the size of the transitive set a node unblocks — a graph computation over data the tree already contains in prose. The hard part is not the graph; it is getting the declarations written without turning every node into a form.

**What would make this wrong.** If most tests turn out to be independent, leverage is near-uniform and the ranking says nothing. The tetrix tree had a 4:1 ratio sitting in it, but that is one tree. The assumption test under this node checks the ratio before anyone builds the graph machinery.

⚠️ Unvalidated. Proposed by an agent, from an agent's behaviour — an operator has not asked for this.

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 unlinked "Hand-compute unblock counts and see if the operator's pick changes" — moved under "Unblock count changes which node an operator actually picks" — the belief this test measures now has a node of its own
