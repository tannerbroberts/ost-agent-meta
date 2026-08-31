---
type: Solution
source: 'TRANSCRIPT:0f28d01f-35fa-49f0-b085-89170e306ef8'
created: '2026-08-18'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[A narrow wait-for-condition primitive covers the polling shapes Monitor currently refuses]]

Give Monitor a structured "wait for condition, then run a follow-up read" primitive — poll interval plus a bounded command, no shell substitution — so a run expresses "wait until this finishes" as a typed call Monitor already knows how to grant, rather than composing an until/sleep shell loop that trips the command_substitution refusal.

## Issues
- 2026-08-31 2026-08-31 unattended sweep, repo sight held: examined for a missing instrument and deliberately left without one. Recording the examination because this node carried no prior note, while both of its siblings on the same transcript source do — a reader meeting one and not the others would reasonably assume this branch had been half-checked. The artefact is Monitor, a harness tool: no spec under this repository's test/ can assert anything about which command grammars it grants, so the mechanical half is structurally out of reach here. This is the identical blocker already recorded on "Monitor states its accepted command grammar up front rather than discovered by refusal" and "A background task's own output directory is automatically readable by the Monitor call that started it". The belief beneath it, "A narrow wait-for-condition primitive covers the polling shapes Monitor currently refuses", is feasibility about someone else's implementation, and the corresponding ask is already on the standing queue as "Ask someone with the Monitor tool's implementation open whether a bounded until sleep primitive is addable without reopening arbitrary shell execution". Worth recording alongside: this firing's own corrections preamble carries a permitted `await '<condition>'` helper on the session PATH, which is this candidate's mechanism already partly delivered by a different surface — evidence about the idea, not a reason to instrument the node. What a human should do: set the lane with `ost-agent lane --set`, since ost_flag_humans_required is withheld on the unattended surface. Not a skipped step.
