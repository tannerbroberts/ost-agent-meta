---
type: Assumption
status: unvalidated
source: 'TRANSCRIPT:6e66c934-24d8-4200-b6f2-7af23002c478'
created: '2026-08-06'
evidence: observed
---
#Assumption #unvalidated #evidence/observed

**Potential harm.** Stated as the thing that could go wrong rather than the thing that will work: if the allowlist is generated from a declaration, then editing the declaration is how you acquire a permission — and the run can edit files.

This is the one failure this project is organised against. The ruleset already carves the same line in three places: the agent may remove work from compute's reach with `ost_flag_humans_required` but only a human's `ost-agent lane --set` may add it; the agent may cite a source but only a human may rank it; the agent may propose a node but only a human may promote it. In every case the permissive direction is the human's. A generator that reads `allowed-tools` and writes a settings file inverts that for the one permission that governs all the others, because a run that can add a line to its own skill frontmatter has granted itself every tool.

It could be false in the ordinary case — and probably is. Generation at install time, by a person running an install command, with the skill frontmatter fixed at that moment, is not self-granting; it is a person choosing once instead of twice. The hazard only appears if the generator can be triggered from inside a session, or if it re-reads the declaration at run time rather than at install time.

So the assumption is not "this is dangerous" but "the dangerous path is reachable", and that is precisely the kind of question a spec file settles and a conversation does not. If the generator refuses to run except from a human-invoked install, and refuses to write when the declaration is newer than the last install, then the objection recorded on the parent solution is answered and the candidate is stronger than its siblings rather than weaker.

Separately doubtful, and not what this assumption covers: whether any operator ever *wants* a narrower grant than the skill declares. If they do, this solution removes a control they were using deliberately, and no amount of safety mechanism makes that right. That is a desirability question, it needs operators, and it is currently unowned.
