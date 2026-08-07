---
type: Assumption
created: '2026-08-07'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Render the tree across a recorded visit and require the second render to name exactly what changed]]

**The belief, stated so it could be false.** A reader's "what changed since I last looked" can be derived from what the vault already holds — the node files, their `## History` lines, and the git commits every write produces — without asking the reader to install anything, without a server keeping per-reader state, and without the agent being asked to remember who visited when.

It could be false in three concrete ways. There may be no durable place to record *when a particular reader last looked* that survives a fresh clone. Git may not attribute a change to a node at the granularity a reader needs — a pass that touches forty files in one auto-commit produces a diff that is technically accurate and useless. And a node's meaningful change (a status transition, a new instrument, a merged duplicate) may not be recoverable from the file diff without re-deriving semantics the writer already knew and discarded.

**Why this assumption exists as a second belief under this solution.** The solution's other assumption — "A rendered tree orients a reader faster than the files do" — is a claim about a person, and no exit code observes it. Four prior passes recorded that correctly and each concluded the solution could not be instrumented. That conclusion was right about *that* belief and wrong about the solution: a rendering candidate rests on a buildable half as well as a human half, and only the human half was ever written down. This node is the buildable half, separated so it can be settled mechanically without a green test being mistaken for evidence that anyone was oriented faster.

**What settling this does not settle.** Nothing about desirability or usability. If this assumption holds, the diff is computable; whether the resulting view is legible at 1071 nodes, and whether structure is what a stakeholder wanted rather than a plain answer to "are we on track?", are untouched and stay with the reader-shaped assumption beside this one.

⚠️ Unvalidated, and authored by an unattended pass that could not read the product repository — `product.repos` is unconfigured and direct reads of the product directory were denied. So the claim that no such mechanism exists today is an inference from this tree's own records, not a verification against the code.
