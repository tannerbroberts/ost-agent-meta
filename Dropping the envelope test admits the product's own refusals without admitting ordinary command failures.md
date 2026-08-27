---
type: Assumption
source: 'agent-run:unattended-sweep-2026-08-27'
created: '2026-08-27'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion
[[An unwrapped MCP refusal is extracted as a correction while a non-zero exit still is not]]

**Risk category: feasibility.**

The belief, stated so it could turn out false: with `GUARD_MARKER` removed, `splitRefusal` alone is a good enough discriminator — it keeps the refusals an `ost_*` tool issues (which name a permitted form and arrive with no `<tool_use_error>` wrapper) and still drops a command that merely exited non-zero (which names no permitted form, wrapper or not).

**How it could be false.** `splitRefusal`'s remedy cues are four ordinary English words — `use`, `must`, `instead`, `try`. A failing command's own output can contain any of them within the last 400 characters and would then be read as advice. The module's docstring records exactly this going wrong once, on a `String to replace not found in file.` message whose quoted payload contained the word "must"; the end-anchoring rule was added to fix that instance. Whether that rule generalises past the instance that prompted it is precisely what is unknown, and it is the whole bet of the candidate above.

**Why this is the sharpest of the risks here.** The candidate's other risks are cheap to live with. This one decides whether the change is an improvement or a regression, because a ledger that fills with non-corrections fails in the same direction the ledger was built to fix — becoming long enough that nobody reads it.

**What settling it does not settle.** Nothing about desirability. A correctly-populated ledger is not evidence that carrying these corrections forward changes what a later session writes, which is a separate belief and would need its own test.
