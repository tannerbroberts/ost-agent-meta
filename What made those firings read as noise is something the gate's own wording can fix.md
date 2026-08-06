---
type: Assumption
status: unvalidated
created: '2026-08-06'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Count how buried each of the three firings was before assuming the wording was at fault]]

**Usability.** The node records three correct gate firings that were each read as noise before they were read as findings. The implicit diagnosis is that the gates said the wrong thing. That is one hypothesis and it is not the only one.

Stated so it can be false: the firings were misread because of what they said. The competing explanation is that they were misread because of where they landed — three signals arriving inside a session that was also producing ordinary progress output, each one a few lines among many, none of them distinguishable in the moment from the surrounding chatter. If that is what happened, then better wording changes nothing, because the reader's failure was not comprehension but triage, and the fix is placement, batching or a hold, not vocabulary.

The two hypotheses want opposite things built. Content says: put the criterion, the observed value and what would clear it into the message. Placement says: stop interleaving gate output with progress output, or hold firings and present them together at a boundary where the reader is deciding rather than watching.

There is a way to tell them apart without asking anybody, and it is cheap: the session that produced these three firings was recorded, so how buried each one was is a countable fact. If each fired in relative isolation and was still misread, the content hypothesis survives and this solution is aimed correctly. If each was buried under dozens of unrelated lines, then the wording was never given a chance and the parent assumption is false.

That check should happen before anything is written, because the two remedies do not overlap and building the wrong one costs a full cycle. This is also the cheaper order: the count is a spec file over data already on disk, and the alternative is asking a person to re-read three messages they have already formed an opinion about.
