---
type: Assumption
status: unvalidated
source: >-
  tree-restructure:2026-08-05 — the belief this solution's test was already
  measuring
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Load the ingest channel at ten times observed peak and check provenance survives]]

Degrading by slowing rather than dropping is the whole design. It fails if identity is what gets lost under load — events that arrive but can no longer say where they came from are worse than events that never arrived, because nothing reports them missing.
