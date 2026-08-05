---
type: Assumption
status: unvalidated
source: >-
  tree-restructure:2026-08-05 — the belief this solution's test was already
  measuring
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Take the harvested commands and count how many genuinely need a shell to do their work]]

Removing the shell removes a class of quoting bug. It also removes pipelines, redirection and substitution. That trade is only good if the commands actually run rarely need those — otherwise composition gets rebuilt above the exec, badly, with new quoting rules to get wrong.
