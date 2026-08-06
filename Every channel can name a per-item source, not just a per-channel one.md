---
type: Assumption
status: unvalidated
created: '2026-08-06'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Refuse a source that names no record, at write time rather than at sweep time]]

**Feasibility.** Ingestion already reports per channel — six lines, one each for inbox, friction, transcript, usage, atlassian and slack, saying what each captured or why it was off. The solution asks for something a level finer: each captured item naming the source inside its channel that produced it.

Stated so it can be false: some channel cannot attribute at item level. The usage channel is the obvious candidate. Its records are mechanical rollups — "108 tool invocations, p50 3ms, 3 sessions" — computed by aggregating across sessions, and an aggregate does not have a source in the way a transcript line does. If the answer for that channel is "three sessions, and this number came from all of them", then per-item attribution is either impossible there or means something different, and the solution's word "every" is doing damage.

There is a second and more damaging way it can be false, and it is already on the tree in the form of a defect: four nodes in this vault cite `TRANSCRIPT:89ac8277-29ce-4d80-827e-cefea0bebabf`, and no evidence record carries that id. So attribution today is not merely coarse, it is unchecked — a source string can name a record that does not exist and nothing refuses it at write time. A channel that names a source it cannot resolve has not attributed anything; it has written a plausible string. Naming sources and being able to resolve them are two claims, and only the second is worth anything.

That is the sharper reading of this solution and the one the test below takes: the useful property is not that each item carries a source field but that every source field resolves to a record that exists, checked when it is written rather than by a hygiene sweep afterwards.
