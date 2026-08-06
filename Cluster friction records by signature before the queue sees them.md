---
type: Solution
source: 'agent-run:autonomous-loop-2026-08-06'
created: '2026-08-06'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

**The idea.** The transcript harvester stops emitting one record per session. It groups friction events by signature — tool name plus error class, so "permission denied on a declared MCP tool" is one signature however many sessions hit it — and emits one record per signature, carrying the count and the contributing session ids.

**Why this one.** It attacks the problem where it is made rather than where it is felt. The 65 records are not 65 observations; this pass read four of them and found four repeating shapes. A queue that showed "permission denied on a declared tool — 41 events across 18 sessions" would be both smaller and more informative than what it shows now, and the operator's original ask — usage feeding back automatically — is better served by a frequency than by a diary.

**How it compares to its siblings.**
- "Let a friction record corroborate an existing opportunity" is the more valuable end state but needs a judgement per record and a new edge type. This one needs no judgement at all: the signature is mechanical, so it works unattended and on a surface with no reasoning budget left.
- "Record a read-and-skipped judgement" is pure disposal. This one preserves the count, which is the part worth keeping.
- Clustering and corroboration compose well — cluster first, attach the cluster — and if both ship this one should ship first because it makes the second one's per-item judgement cost fall by an order of magnitude.

**Where this fails, stated so it can be judged rather than assumed.** A signature is a guess about what makes two events the same, and the interesting friction is often the singleton. The `clarifying_question` in session `2a4bcf6e` — an unattended firing stopping to ask a human which of three ways to proceed — appears once and matters more than the fortieth permission denial; a frequency-ranked queue buries it. Clustering also destroys the narrative inside a session, and some of these records are only legible as a sequence: read three retries followed by a denial and you can see what the agent was trying to do, which a bag of counts loses. Worst case it makes the queue tidy and the tree blind to exactly the events worth reading.

**Cost.** A signature function and a change to the harvester's emit step. The cheapest of the three, and the only one that changes nothing about the tree's data model.

⚠️ Unvalidated. Nobody has confirmed that a count is what the operator wants from self-observation rather than a readable account of what went wrong.
