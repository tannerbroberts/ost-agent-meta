---
type: Assumption
source: 'first-party-observation:2026-08-05 unattended pass'
created: '2026-08-05'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Check the guard refuses an unaccounted-for section drop and permits an acknowledged one]]

Feasibility, with a false-positive rate attached. The belief is that "the caller did not account for this section" is a decidable condition that separates the destructive call from the legitimate one, and that the separation is clean enough for the refusal to be worth its cost.

Stated so it could be false. A guard that fires whenever a heading is missing will fire on every caller who consolidates two sections into one, retitles a section, or folds a section's content into running prose — all of which are legitimate rewrites and all of which look identical to an accidental drop from the outside. If those are common, the guard becomes noise, and a refusal that fires mostly on honest work is a refusal callers learn to route around rather than read.

This vault has direct evidence the cost is real: its own census records thirteen separate sessions independently rediscovering one refusal, and one session hitting an identical refusal five times in a row. Refusals here are not reliably read even when they are correct. So the bar for this one is not "does it catch the drop" — it is whether it can catch the drop while staying quiet enough that a caller has not already stopped listening.

## Provenance

First-party observation made during the unattended maintenance pass of 2026-08-05, which reproduced the silent `## History` loss on itself. No stored evidence record exists for it, so the source is free text rather than a citation the vault cannot resolve.

## History
- 2026-08-05 merged "A guard can catch the unacknowledged drop without refusing honest rewrites" into this node and deleted its file — Same belief, same wording — the original was created minutes earlier in this pass with a fabricated provenance id (`TRANSCRIPT:2026-08-05-unattended-pass`) matching no stored evidence record, reported by `ost_check` as an unresolved-citation violation. `source` is frontmatter with no setter on this surface, so re-creating with truthful free-text provenance and folding the original in is the only available repair. The merge carries the original's edge to its assumption test across.
