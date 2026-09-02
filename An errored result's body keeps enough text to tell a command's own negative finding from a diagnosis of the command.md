---
type: Assumption
source: 'agent-ideation:2026-09-02-unattended-sweep'
created: '2026-09-02'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion

**Category: feasibility.**

The belief, stated so it could be false: the text the adapter receives in an errored `tool_result` still contains the material that separates the two cases — a broken command's diagnostic line survives, and a clean negative answer arrives without one — so a pattern can discriminate them.

**Why it could be false, concretely.** `resultText()` takes whatever the host put in `block.content`, and the evidence records show it heavily condensed: `Exit code 1 … Tests 3 failed | 7 passed (10)`. If the host clips a long Bash result to a head and a tail before it is ever persisted, a diagnostic printed in the middle is gone by the time the adapter sees it, and every long-output failure looks exactly like a clean negative. The demotion would then be silently wrong in one direction only — always towards calling failures observations — which is the worst shape for this defect to take.

**A second way it could be false, already half-visible in the code.** `ERROR_LINE` matches `no match`, `not found` and `failed`, which is the vocabulary of a *successful* negative answer. So the existing helper's notion of an error line is evidence that the two vocabularies overlap, not that they separate. Whether a narrower diagnoses-the-command pattern can be written without dragging those words along is exactly what is in doubt.
