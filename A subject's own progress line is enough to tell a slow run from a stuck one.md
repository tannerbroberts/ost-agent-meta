---
type: Assumption
source: 'agent-ideation:2026-08-29-unattended-sweep'
created: '2026-08-29'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion

**Risk category: feasibility.**

The belief, stated so it could turn out false: when a wait expires, the subject's last emitted progress line and its age are enough for the caller to choose correctly between waiting again and stopping.

**Why it could be false.** Plenty of stuck processes keep emitting. A test runner that has hung on one file still prints nothing new but is alive; a runner deadlocked in a retry loop may print steadily forever. Conversely a healthy compile can go quiet for minutes during a single long step, which under this rule reads as stuck. If the gap between "last line 6s ago" and "last line 280s ago" does not in practice separate the two cases, the heartbeat adds a number without adding a decision, and the caller is exactly where it started.

**This is the belief the parent solution rests its whole argument on** — that the information the waiter lacks "exists in plain text one process over." If the plain text is there but not discriminating, the candidate fails even when fully built.

Not the only belief beneath that solution: it also assumes every long-running command can be launched in the heartbeat-emitting form, and that the subject is a local process at all. Those are named in the solution's own prose and are not carried by this node.
