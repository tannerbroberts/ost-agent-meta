---
type: Assumption
source: 'agent-ideation:2026-09-07-unattended-sweep'
created: '2026-09-07'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion

**Risk category: feasibility.**

The belief, stated so it could be false: `.ost-agent/usage/events.jsonl` plus the declared `loop.cadence` contain everything needed to state, correctly, how long it has been since a firing — with no new record written and no new process run.

**How it could turn out false, and this is the specific hazard.** The trace records *tool invocations*, not firings. A firing that started, did its reading and decided there was nothing to do could in principle record nothing, and would then be indistinguishable from a firing that never happened. If that case is common, a liveness line computed this way reports outages that did not occur, and a false alarm on a healthy loop is worse than the silence it replaces — it trains the operator to ignore the line.

It could also be false in the other direction. This vault's own MCP surface records every call, so on the observed 2026-09-04 to 2026-09-06 gap the trace held zero events across three days and the inference was sound. Whether that holds for a firing on a differently-configured surface — one whose tools are not all traced — is exactly what is unestablished.

**Why this is the belief worth testing and not the rendering.** Putting a number in a response is trivial. Whether that number means what it says is the entire question, and it turns on whether "no invocations" and "no firing" are the same event.
