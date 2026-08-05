---
type: Opportunity
status: unvalidated
source: >-
  tree-restructure:2026-08-05 — split from the bucket that held these solutions
  directly
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion
[[Validate every tool call against the schema the tool already declares]]
[[Refuse a write whose content is empty or literally undefined]]
[[Echo the written line back so a bad write is visible immediately]]

Nothing between composing a call and its effect on disk inspects what is about to be written. A wrong argument name, an empty body, a literal `undefined` — each is accepted, written, and discovered later by reading the file. The check that would have caught it is a check the tool already has the schema for.
