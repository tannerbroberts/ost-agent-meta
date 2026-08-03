---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

The run declares itself unattended to everything it invokes — the environment variables, the flags, the config that tell a tool no terminal is watching — and anything that would still prompt is made to exit with an error instead. The run then fails in a way its supervisor can see, rather than hanging in a way nobody can.

Turning a silent stall into a loud failure is the whole gain. A failure is reportable, retryable, and countable; a hang is none of those, and the evidence shows one costing an entire run twice.

**Compared to the alternatives.** Simple, uses mechanisms that already exist in most tools, and it never guesses at an answer on the operator's behalf. It converts the stall into a stop rather than letting the work continue, so a run that hits a prompt still achieves nothing — it just says so promptly.

**What would make this the wrong pick.** It relies on every invoked tool honouring the convention, and the ones that ignore it are exactly the ones that caused the problem. A git that prompts for a reconcile strategy despite a non-interactive environment will hang exactly as before, and the run will now believe it cannot.
