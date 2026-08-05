---
type: Assumption
status: unvalidated
source: >-
  tree-restructure:2026-08-05 — the belief this solution's test was already
  measuring
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Maintain a sweep from returned deltas alone across a full pass and compare against a fresh read]]

This is correct only while the caller is the sole writer. In a shared vault a locally maintained picture drifts silently — and the re-read it replaces was the thing that would have caught the drift.
