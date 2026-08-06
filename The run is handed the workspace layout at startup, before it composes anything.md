---
type: Solution
source: 'agent-ideation:2026-08-06-unattended-sweep'
created: '2026-08-06'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

**The idea.** The run receives a generated inventory of the workspace as part of its opening context — the directories that exist, the test suite's layout, whether this is a git repository, which roots are readable at all. It composes against a description rather than a belief.

**Why this shape.** Every failure in the parent opportunity's census is a *well-formed* command against a path the agent believed in: `sed: src/cli/index.ts: No such file or directory`, `git` returning 128 from a directory holding only `bin/` and `vaults/`. The belief was never checked because checking it costs a turn, and the turn is only obviously worth spending after the command has already failed. Moving the cost to startup makes it a fixed charge instead of a per-guess one, and it is paid by the party that already knows the answer.

**How it differs from its siblings.** This is the push form: the layout arrives unasked. "Require a path to have been observed before a command may address it" is the pull form — it makes the run go and look, and it catches paths the manifest did not anticipate. "A path refusal names the nearest real candidates" prevents nothing and instead makes the first failure carry the layout, which is the only one of the three that helps a run whose beliefs were wrong in a way nobody predicted.

**Where it fails, stated so it can be judged.** An inventory of a large repository is either too coarse to answer the question that matters or too large to carry, and this pass has the receipt: `ost_read_tree` was refused at 134,240 characters for exactly that reason. It is also stale from the moment it is generated, and a run that edits files during its own pass will diverge from it. Worst, it is a second statement of the workspace's shape that can drift from the workspace — the same defect recorded under "A guard derived the rule it was checking, so it agreed with the bug for 23 releases".

**A limit this specific pass can attest to.** An inventory would not have helped the case observed here. This sweep's reads of the product repository were refused for *permissions*, not absence — the path was right and the grant was missing. A layout manifest describes what exists; it says nothing about what this run may read, and those are different failures with the same error surface.

**Cost.** A generator plus context budget at startup, on every run, whether or not the run touches a file.

⚠️ Unvalidated. Agent-ideated from the agent's own transcripts — usability evidence, not evidence that anyone wants this.
