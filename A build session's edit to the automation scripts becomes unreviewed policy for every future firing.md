---
type: Opportunity
source: 'INBOX:2026-08-16-audit-loop-efficiency-and-checkout-drift.md'
created: '2026-08-16'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion
[[Reset the shared checkout to main before every firing reads which script to run]]
[[Give each firing its own isolated worktree, so no firing inherits another's checked-out state]]

**The need (operator's voice, inferred from an audit session's finding):** "My build and discovery loops both run their automation scripts directly out of one shared working directory with no worktree isolation. A build session's first step is `git checkout -b <branch>`, and that branch stays checked out after the session ends — observed: this repo sat on a stuck solution's branch for its whole stuck period, so every later firing of both loops ran automation code from that branch rather than from reviewed `main`. In this instance it was harmless, but the build agent has unrestricted `Write` against the whole repository, including its own policy scripts (`examples/automation/*.sh`). Nothing stops a future build session from editing that script, leaving its branch checked out, and having its own unreviewed edit become the executable policy for every subsequent firing of both loops with no review in between."

**Why it matters:** this is a self-modification risk with no review gate — the mechanism that is supposed to keep the agent's actions bounded (a human-reviewed script) can be silently rewritten by the very agent it bounds, simply by the shared checkout not resetting between firings. It is a sharper instance of the trust concern this branch already holds: not two writers racing on one file, but one writer's transient state quietly becoming the next run's law.

**Litmus (more than one way?):** yes — reset the shared checkout to `main` at the start of every firing, before reading which script to run; give each firing worktree isolation; deny `Write` on the automation-script paths to the build agent's own grant; require the policy scripts to be pulled from a signed/reviewed ref rather than the working tree; a preflight check that diffs the checked-out script against `main` and refuses to proceed if they differ.

**Provenance caveat:** the drift itself is observed (this repo did sit on the wrong branch for the stuck period). The exploit — a build session editing its own policy script and having that edit persist unreviewed — is inferred, not observed: no session has done this. Evidence class recorded at the weaker rung accordingly.

_Source: INBOX:2026-08-16-audit-loop-efficiency-and-checkout-drift.md, "A risk noticed, not yet acted on: shared-checkout branch drift" — from an attended audit session's direct observation of the shared checkout and the build agent's grant._
