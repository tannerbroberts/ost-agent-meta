---
type: Assumption
source: 'agent-ideation:2026-10-17-unattended-sweep'
created: '2026-10-17'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion
[[One tool_use id written on two lines files no retry, while two ids with one signature still file one]]

**Risk category: feasibility.**

**The belief, stated so it could be false:** if `extractFriction` skips any `tool_use` block whose id it has already seen, the second copy of a parallel call files nothing. Meanwhile two separate calls with the same name and input, each under its own id, still file exactly one retry.

**How it could be false.** The host could reuse an id across distinct calls, for example after a resumed session. Then real repeats would vanish. Or the fix might be applied only to the retry branch, so a copied `tool_result` still double-counts as `tool_error`. A spec can check the second case directly. The first rests on the host's id contract, which this repository does not own.
