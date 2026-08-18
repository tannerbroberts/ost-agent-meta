---
type: Assumption
created: '2026-08-18'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion

Removing dist/ from source control only helps if every consumer of this repo (an installer, a plugin loader, a downstream script) either runs its own build step first or doesn't need dist/ to exist between firings. If any consumer today installs or loads directly from the committed dist/, removing it breaks that consumer the moment it runs against a fresh checkout with no build step of its own.
