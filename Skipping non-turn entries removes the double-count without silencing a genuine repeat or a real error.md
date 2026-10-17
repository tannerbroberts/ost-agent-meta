---
type: Assumption
source: 'agent-ideation:2026-10-17-unattended-sweep'
created: '2026-10-17'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion

**Risk category: feasibility.**

**The belief, stated so it could be false:** every tool call a session really makes, and every `tool_result` with `is_error: true`, appears in a line whose `type` is `assistant` or `user`. So filtering to those two types removes the api-request-blob copies and nothing anyone would have wanted.

**How it could be false.** A real turn might only be recorded in a non-turn line, for example after compaction or in a subagent sidechain. Then the filter silently drops real friction. That is a worse failure than the double-count it fixes, because an over-count is visible and an under-count is not.

**What a spec can and cannot settle here.** A spec can show the code ignores a blob copy and still reports a real repeat and a real error from turn lines. It cannot show the host never puts a real turn somewhere else. That half rests on the host's transcript format, which this repository does not own.
