---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

A mutating call already knows what it changed about the outstanding picture. Creating a solution under an under-served opportunity moves that opportunity's count and adds a solution with no assumption test. Return that as part of the write's own result, and a caller can maintain an accurate sweep locally without asking for one.

The re-reads exist because writes currently answer only "done" when they could answer "done, and here is what that changed."

**Compared to the alternatives.** Removes the calls entirely rather than making them cheap, which is the only version of this that shows up in a trace. The caller's picture also stays current continuously instead of in jumps. The cost is that every write must compute its consequences correctly, and a write that computes them wrongly leaves the caller confidently out of step with the tree — a failure with no symptom until something surprising happens.

**What would make this the wrong pick.** It is only correct while the caller is the sole writer. In a vault two agents share, a locally maintained sweep drifts silently, and the re-read this replaces was the thing that would have caught it.
