---
type: Opportunity
source: 'agent-run:autonomous-loop-2026-08-06'
created: '2026-08-06'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion
[[Drop shipped solutions from the instrument queue]]
[[Ask a shipped solution for its observed exit code instead of an instrument]]
[[Refuse an instrument that passes on arrival]]

**The need.** When I finish a piece of work and record it as finished, the queue should stop asking me for it. Right now it does not, so every pass re-reads the same items, and the pass cannot reach `done` no matter how much real work gets done.

**What was observed, and how.** This pass read `solutionsMissingInstruments` (64 solutions, 25 shown) and then grepped the vault for `status: shipped`. Ten nodes in the whole vault carry that status. Five of them were in the 25 shown:

| Solution | status |
|---|---|
| A result must state what it did not cover | shipped |
| Post-session transcript harvester | shipped |
| Refuse a proving command whose exit code cannot report failure | shipped |
| Refuse a wiki-link that contains a newline | shipped |
| Refuse a write whose content is empty or literally undefined | shipped |

So 5 of 25 shown — 20% of the visible queue, and half of every shipped node in the vault — are being asked for an instrument. The remaining 39 unshown may hold more.

**Why this is unsatisfiable rather than merely annoying.** The queue asks for a command that is RED today and goes green when the solution is built. For a solution that is already built, no such command exists: any honest spec asserting the shipped behaviour passes on arrival, so it cannot fail, measures nothing, and hands a builder no definition of done. The instruction and the node's state contradict each other, and the only ways out are to invent a command that fails for a bad reason (the file is missing) or to do nothing. Both leave the item in the queue for the next pass.

**What it costs.** The 2026-08-05 sweep hit this on "Refuse a wiki-link that contains a newline", worked out that an instrument was impossible, corrected the status to `shipped` instead — and the node is in this pass's queue anyway. That is the whole cost in one example: a pass paid attention to reason it out correctly, recorded the right answer, and the queue did not read it. Every future pass pays that again, and a pass that reasons less carefully pays it by writing a green-on-arrival instrument, which is worse than paying it twice.

**Why it belongs under this parent.** The parent's complaint is that the pass never declares itself done, so the operator cannot tell when to stop paying for compute. This is one identified mechanism behind that: a queue that does not drain when the work is done. It is not the only one, but it is the only one this pass could demonstrate from the tree's own output rather than infer.

**Litmus test.** More than one way to address it: drop shipped nodes from the queue, change what the queue asks a shipped node for, or refuse the wrong answer at the write boundary. Three candidates sit beneath this, and they differ in what they believe the queue is for.

⚠️ Unvalidated. Distilled by an unattended pass from the tool's own output; no human has confirmed that a draining queue is what they want, and one could reasonably argue a shipped solution still owes evidence that it works.
