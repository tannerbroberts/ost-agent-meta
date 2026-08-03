---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Take the last ten regretted writes and check whether each could have been refused mechanically]]

When a human finds a write that should never have been accepted, the response is not to fix that node but to write the check that would have refused it, and add it to the set every mutating call runs before touching disk. The backlog of regretted writes becomes the specification for the refusal set.

The vault already works this way in places — reserved headings that no argument may contain, a status value that simply does not exist on the tool, an evidence ceiling enforced at the call. Each of those is a lesson that became a mechanism. This proposes making that conversion routine rather than occasional.

**Compared to the alternatives.** The only option that reduces the number of bad writes rather than managing them afterwards, and the only one whose benefit compounds — every invariant added protects every future call for free. It is also the slowest to pay off, since it can only learn from mistakes already made, and it does nothing whatsoever for the write that is on disk right now. Retraction and this one are natural partners: retract the instance, then add the invariant.

**What would make this the wrong pick.** Invariants are themselves permanent and accumulate. A refusal set grown one regret at a time will eventually refuse something legitimate, and the person hitting that refusal will have no idea which past mistake they are being protected from.
