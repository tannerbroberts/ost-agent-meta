---
type: Solution
status: unvalidated
created: '2026-08-02'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

Change the packaging rather than the configuration: make the vault itself carry what is needed to operate on it, so that opening the vault anywhere yields the tools, with no separate enabling artifact in a directory that may or may not be the one the session opened.

**Compared with the alternatives:** this is the only candidate that survives the vault being moved, copied, or opened from an unexpected working directory — the class of problem the observed failure actually belongs to, since the plugin was declared correctly and simply never launched. It is also the most invasive, it constrains how the product can be distributed, and it may not be achievable within the host's plugin model at all. That last point is the feasibility question worth settling before anyone builds it.

Unvalidated, agent-ideated: a candidate for comparison, not a recommendation.
