---
type: Assumption
source: 'agent-ideation:2026-08-06-unattended-sweep'
created: '2026-08-06'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion

**The belief, stated so it could be false.** Storing the probe command beside a recorded literal keeps the recording honest, because someone re-takes the observation when it matters.

**Why it is the riskiest one.** A stored command that nothing runs is a comment, and this repository has a documented instance of exactly that failure — the file naming the prefix defect "had been written in an earlier session and never committed... the finding existed, on disk, unread, for days." The whole solution trades a derivation that is *wrong now* for a recording that is *right now and rots later*, and it is not obvious that is a good trade unless something forces the re-take. If nothing does, this replaces a guard that agrees with the bug with a guard that agrees with last year's runtime, and the second failure is quieter.

**What class this is.** Feasibility. Answerable by running the stored probes and comparing.

**How it could come out false — usefully.** If re-taking is cheap enough to do on every CI run, the solution should say so and require it, which converts the stored command from documentation into a scheduled check and removes this risk entirely. That is a better version of the solution and testing this is how it gets found.
