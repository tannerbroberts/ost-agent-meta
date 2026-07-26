---
type: Solution
source: 'agent-ideation:2026-07-26-tenth-pass'
created: '2026-07-26'
evidence: assertion
---
#Solution #evidence/assertion
[[Does an operator notice a bad write when the tool echoes the line back]]

**The idea.** A mutating tool returns the line it actually wrote, not a confirmation that it wrote something. `annotated "Some node"` becomes `annotated "Some node": - 2026-07-26 undefined`.

**Why this one is interesting despite being the weakest.** It is the only candidate here that would have surfaced the defect **at the moment it happened, to the party that caused it**, with no rule and no schema — the caller reads its own output and sees the word `undefined` in it. The other two prevent this specific failure; this one shortens the distance between *any* bad write and its discovery, including failures nobody has predicted.

**Prior art in this codebase, and it works.** `ost-agent lane --set` already returns the exact History line it appended, and `ost-agent result` prints the recorded line plus its uncovered clause. Those surfaces have never produced a silent bad write. `ost_annotate` returned `annotated "<title>"` — a confirmation that the call completed, which is precisely the thing that was true.

**Where it fails.** It relies on somebody reading the output. An unattended pass discards tool output routinely — this pass would very likely have skimmed past it — so as a sole defence it is weak. As a *third* layer behind a schema check and a write guard, it is nearly free.

⚠️ Unvalidated. Agent-ideated.
