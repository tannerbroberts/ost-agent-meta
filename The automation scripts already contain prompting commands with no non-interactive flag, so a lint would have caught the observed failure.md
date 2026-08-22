---
type: Assumption
status: unvalidated
source: 'agent-ideated:2026-08-22-unattended-sweep'
created: '2026-08-22'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion

**The belief, stated so it could be false:** the defect this solution proposes to lint for is present in the checked-in automation today, and a lint over `examples/automation/*.sh` would have refused the firing that produced the founding evidence.

**Why it could be false, and why that matters more than it looks.** If every prompting command in those scripts already carries its flag, then the prompt in session `005ca37f` came from somewhere a script lint cannot see — a command the agent composed ad hoc mid-run — and the whole solution is aimed at the wrong surface. That is not a small correction: it would mean the lint is real, correct, and irrelevant, and it would move the answer to one of the siblings, which act at run time rather than at authoring time. This is the single fact that decides whether this candidate is worth building at all, which is why it is stated as its own belief rather than assumed inside the solution's prose.

**What is already known, and what is not.** `examples/automation/` holds exactly three files (`autonomous-pass.sh`, `build-pass.sh`, `github-workflow.yml`), confirmed by a first-party listing this pass. None of the three was read line by line here, so whether any prompting command in them lacks its flag is exactly the open question — and the founding evidence's `overwrite src/cli/index.ts?` is the signature of an un-flagged `cp` or `mv`, which is suggestive and not proof of where it lived.

**Category:** feasibility.
