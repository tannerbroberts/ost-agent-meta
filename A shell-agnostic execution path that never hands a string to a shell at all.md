---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

Commands are given as a program and a list of arguments, executed directly, with no shell between the caller and the process. There is no quoting layer to get wrong, no glob to be expanded by rules the caller did not expect, and no difference between what one shell does and what another does — because no shell is involved.

Every failure in the evidence lives entirely in that layer. A comparison misparsed, a glob that matched nothing and aborted the command, a newline inside quotes, a sentence swallowed. None of them is about the work; all of them are about the intermediary.

**Compared to the alternatives.** Eliminates the class completely and permanently, which neither a counter nor a better affordance can claim, and it removes the whole surface rather than the cases anyone anticipated. It is also the most disruptive: pipelines, redirection, and expansion are genuinely useful and would each need an explicit replacement, and callers used to writing shell would have to stop.

**What would make this the wrong pick.** A lot of real work is a pipeline. Rebuilding composition, redirection, and substitution above a shell-less exec means reimplementing a shell badly, and the second system will have its own quoting rules that people get wrong in new ways.
