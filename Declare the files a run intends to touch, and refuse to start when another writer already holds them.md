---
type: Solution
source: 'TRANSCRIPT:424486ec-3489-4b53-8e2b-012232d221ab'
created: '2026-08-06'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A tree being moved by another writer can be told apart from an operator simply working]]

**Candidate solution (unvalidated).** Before doing any work, a run states the paths it intends to write and checks whether anything else is currently holding them — uncommitted changes with recent mtimes, an in-flight merge, a rebase or merge state in `.git`, another run's lease. If the ground is already moving, the run declines to start and says so, instead of beginning work it will have to abandon halfway.

**Approach:** *prevent the interleaving*, rather than detect or explain it.

**Contrast with siblings.** The other two candidates accept that the collision happens and differ only in how early the run finds out. This one trades throughput for certainty: it will refuse runs that would have been fine, because "fourteen files touched seconds ago" is a description of an active merge and also a description of an operator who is simply working. That false-stop rate is the whole question about it, and it is what the test beneath it measures.

**Relationship to work already in the tree.** "Two agents sharing my vault can trample each other" carries the lease/queue family for two OST loops writing one vault, and the solutions there are about arbitration between cooperating processes. This is the uncooperative case: the process that moved the ground in the observed session was a pull-request merge, which will never take a lease and cannot be asked to. A preflight that only understands leases would have seen nothing. Named here rather than linked, so the two branches stay separable.

**Where it fails.** It is a check at one instant. Nothing stops a merge landing one second after the preflight passes, so on its own it converts some collisions into refusals and leaves the rest exactly as they are. It is the weakest of the three unless paired with the sentinel — which is an argument for building it second, not first.

⚠️ Unvalidated, and ideated by an agent from its own session record. This grounds usability, not that anyone outside wants it.
