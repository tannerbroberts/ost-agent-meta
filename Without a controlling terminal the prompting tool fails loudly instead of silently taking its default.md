---
type: Assumption
status: unvalidated
source: 'agent-ideated:2026-08-22-unattended-sweep'
created: '2026-08-22'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion

**The belief, stated so it could be false:** removing the TTY changes the *visibility* of the outcome, not just the outcome. The claim is that a tool which today prints `overwrite …? (y/n [n])` and exits 1 having done nothing will, with stdin closed and no controlling terminal, either do the work or fail with a message a run can classify — rather than reaching the same silent default by a different route.

**Why it could be false, which is the point of writing it down.** Three ways:

1. A tool that already checks `isatty` may treat "no terminal" as exactly the same case as "user pressed enter" and take the identical default. Then nothing is gained: the run still silently does not overwrite, and the fix is cosmetic.
2. A tool that reads `/dev/tty` directly rather than checking stdin will not see the closed stdin at all, and with no terminal it may **block** rather than fail. That is worse than today — a stalled firing instead of a wrong one — and it is the failure this solution's own body names as its risk.
3. The behaviour may be per-tool with no common rule, in which case "run without a TTY" is not one guarantee but a per-tool audit wearing the costume of a general one.

**Category:** feasibility. It says nothing about whether losing the work (a loud no) is acceptable to the operator, which is the desirability question this solution shares with its siblings.
