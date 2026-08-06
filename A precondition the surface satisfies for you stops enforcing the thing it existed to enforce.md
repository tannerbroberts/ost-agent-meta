---
type: Assumption
source: 'TRANSCRIPT:57249c25-2e61-480d-b234-007ddf101fa3'
created: '2026-08-06'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Auto-satisfy a read-before-write, then change the file underneath and require the write to still refuse]]

**The belief, stated so it could be false.** A surface that quietly performs the prerequisite read on the caller's behalf loses nothing, because the read was pure ceremony.

**Why it is the riskiest one.** It is probably wrong, and this vault has the record that says so. Read-before-write is not ceremony: it is what makes "has been modified since read" detectable. Session `57249c25` recorded both refusals in one run — three read-before-write collisions and one *stale-read* collision — which is precisely the pair that shows the handshake carrying real information. A surface that auto-reads immediately before writing would satisfy the letter of the precondition and destroy the staleness check, because the read it performs is always fresh. The result is a run that never sees a refusal and silently overwrites a concurrent edit, which is a strictly worse failure than the one being removed and one this tree already names under "The file changed after I read it, and the failed edit is how I find out".

**What class this is.** Feasibility, with a safety edge. Answerable entirely from the repository: does an auto-satisfying path still refuse a write whose target changed between the caller's read and the write?

**How it could come out false — meaning, how the solution survives.** If the auto-satisfaction is scoped to preconditions that carry no detection duty (a closed parameter set, a size probe, a manifest fetch) and explicitly excluded from the ones that do, the solution stands with a narrower claim. That narrowing is the useful outcome of testing this, and it is not what the solution currently says.
