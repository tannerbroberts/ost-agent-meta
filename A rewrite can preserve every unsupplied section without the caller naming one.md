---
type: Assumption
source: 'first-party-observation:2026-08-05 unattended pass'
created: '2026-08-05'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Edit a node holding five sections, supply two, and check the other three survive intact]]

Feasibility. The belief is that a rewriting tool can tell which `## ` sections the caller's `prose` addresses and which it does not, reliably enough to carry the rest across untouched — and that doing so requires nothing of the caller, no extra argument and no prior read.

Stated so it could be false, which it might be. The parse has to survive sections whose headings the caller reproduced but whose bodies they rewrote, headings that appear inside fenced code blocks, and headings that differ only in trailing punctuation or case. If matching is by heading text and a caller retitles a section, the rule sees a removal and an addition rather than an edit, and carries the old one across beside the new — producing a duplicate rather than a loss. That failure is quieter than the one it replaces and is the specific way this assumption goes wrong.

It is worth noting the current mechanism already does this for three headings, so the capability is not in question; what is in question is whether generalising it from a fixed list to *everything unsupplied* stays correct.

## Provenance

First-party observation made during the unattended maintenance pass of 2026-08-05, which reproduced the silent `## History` loss on itself. No stored evidence record exists for it, so the source is free text rather than a citation the vault cannot resolve.

## History
- 2026-08-05 merged "A rewrite can preserve every unsupplied section without the caller naming any of them" into this node and deleted its file — Same belief, same wording — the original was created minutes earlier in this pass with a fabricated provenance id (`TRANSCRIPT:2026-08-05-unattended-pass`) matching no stored evidence record, which `ost_check` reported as an unresolved-citation violation. `source` is frontmatter with no setter on this surface, so re-creating with truthful free-text provenance and folding the original in is the only available repair. The merge also carries the original's edge to its assumption test across.
