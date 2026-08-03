---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

A helper declares what it needs — this interpreter at this version, these commands present — and installing it checks those needs against the machine it is being installed on. A helper that cannot run here does not get installed, and the refusal names exactly what is missing and what version was found instead.

The failure being prevented is a silent bet: the script was written against bash 4, installed on a machine shipping bash 3.2, and nothing between those two moments compared them. Install time is the natural place for that comparison, because it is the last moment when the machine and the requirements are both in view.

**Compared to the alternatives.** Catches the problem at the earliest point where it is knowable, and produces a refusal a person can act on rather than a runtime error mentioning a builtin they have never heard of. It only covers requirements someone remembered to declare, and an undeclared dependency passes install and fails exactly as before.

**What would make this the wrong pick.** Requirement declarations rot. A script that grows a `mapfile` six months after its manifest was written will install cleanly and fail at line 21, which is the original problem with an extra file to maintain.
