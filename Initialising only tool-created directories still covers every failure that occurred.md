---
type: Assumption
status: unvalidated
source: >-
  tree-restructure:2026-08-05 — the belief this solution's test was already
  measuring
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Check whether initialising only tool-created directories still covers every captured failure]]

Removing the variance is cleaner than detecting it, but unconditional `git init` reaches directories the tool did not make. The narrowed rule is safe only if no scaffold target in the record sits inside an existing repository — and it still has to cover the captured failures.
