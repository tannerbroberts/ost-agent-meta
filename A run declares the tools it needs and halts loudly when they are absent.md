---
type: Solution
source: 'agent-ideation:2026-08-02-maintenance-pass'
created: '2026-08-02'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Check whether a toolless session can even run the tool check]]

**The idea.** A scheduled task names its required tool surface up front — for this vault, the `ost_*` MCP tools. Before doing any work, the run checks that they are present. If they are not, it exits non-zero with a message naming exactly which tools are missing and what enables them. The pass never starts.

**Why it addresses the need.** The observed cost was not that the tools were missing; it was that a toolless pass looked identical to a successful one. It ran `check`, reported PASS on 241 nodes, and exited clean while the actual mandate went untouched — four times before anyone diagnosed it. A halt converts twenty-two silent passes into one loud failure on the first day.

**Precedent in this tree.** This is the same shape as [[A check with an empty subject is a failure, not a pass]] applied one level up: there, a sweep with no subjects must not report zero findings; here, a pass with no tools must not report a clean run. If that pattern is right for a sweep it is right for the pass containing it.

**Where it fails, stated honestly.** It is all-or-nothing, and so inherits exactly the criticism its sibling concedes about itself — it fires on total absence and is silent on partial. A surface that has ten of thirteen tools passes the check and then fails in the middle on the eleventh. It is also the most annoying option: a run that halts produces nothing at all, and on a surface where the tools are legitimately unavailable this converts a partly-useful CLI-only pass into no pass. Whether that trade is right depends on whether a CLI-only pass was ever worth its compute, which nobody has measured.

**Cost.** Small. A declared list and a startup check.

⚠️ Unvalidated. Agent-ideated from four consecutive observed failures, 2026-08-02.
