---
type: Assumption
source: 'agent-ideation:2026-09-08-unattended-sweep'
created: '2026-09-08'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion
[[The index adapter answers a symbol query with zero child processes spawned]]

**Risk category: feasibility** — a question about what can be run inside this product's stated constraints, not about what anybody wants.

The belief, stated so it could turn out false: *at least one mature code index is distributed in a form this tool surface can call directly — in-process, no child process spawned — so that "adopt rather than build" is a real description of the work.*

Why it could be false, and this is the assumption most likely to kill its own candidate. The obvious indexers are programs first and libraries second or not at all; the ecosystem's habit is to ship a binary you invoke. This repository's CONTRIBUTING.md forbids adding a tool that shells out, and that constraint is load-bearing rather than stylistic on a surface designed so an agent cannot execute arbitrary things. If every candidate index is a binary, then adopting one means introducing a subprocess boundary and a policy exception — at which point the adapter is not a thin layer over something bought, it is the build, and the candidate's whole claim to being the cheap-by-adoption option is gone.

Note what this assumption does *not* ask. It says nothing about whether the index is any good, whether symbol questions dominate string questions, or whether the index staleness problem is manageable. Those are separate beliefs and each would need its own test. This one is first only because a refuted verdict here retires the candidate before any of them need answering.
