---
type: Assumption
source: 'agent-ideation:2026-08-07-unattended-sweep'
created: '2026-08-07'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[A re-armed permit is refused when the spec file changed underneath it]]

**Kind: feasibility, and it is the hole in this candidate rather than a formality.**

**The belief, stated so it could be false.** Re-arming rests on the claim that an identical command string measures the same thing it measured before. It does not, necessarily. A spec file's contents can change between the observation and the restoration; the command is a pointer, not the measurement. If the repository moved underneath it, re-arming hands back a verdict earned against code that no longer exists, which is precisely the laundering the un-clearing rule was built to stop.

Byte-identity of the command is therefore the wrong identity condition, and the right one is probably identity of what the command resolves to — which is a much stronger requirement and may not be cheaply available.

**What would make it false.** A case where the command string is unchanged, the spec file's contents are not, and the re-armed permit reports a verdict the current code would not produce.
