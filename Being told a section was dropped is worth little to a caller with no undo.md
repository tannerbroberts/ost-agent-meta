---
type: Assumption
source: 'first-party-observation:2026-08-05 unattended pass'
created: '2026-08-05'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Check every dropped section is reported with enough to restore it]]

Stated deliberately in the direction that would kill its own solution, because that is the honest way round. The belief this solution needs is that a caller told `dropped: ["## History"]` will do something about it. The belief stated here is the opposite, and it is the one with evidence behind it.

An unattended pass has no undo. Told what it destroyed, its only remedy is to reconstruct the content from what it still holds in context. On 2026-08-05 that worked exactly once, and by luck: the pass had read the whole file minutes earlier for an unrelated reason and could restore four `## History` entries verbatim. Had it edited from the tool's own listing — the normal case — the report would have named a loss the caller had no copy of, and the response would have been to write "a section was lost here" into the node, which is a worse artifact than the loss.

So the risk is specific and it is not "nobody reads the report". It is that **reporting converts a silent loss into a documented one without changing the loss rate**, and a team looking at a tool that now names its own damage may reasonably conclude the damage is handled. That would make this solution actively harmful relative to doing nothing, because it spends the attention that the two preventive siblings need.

What would make it false: a caller that can act. If the report carried the dropped content itself, or a git ref to it, restoration becomes mechanical and the objection collapses. That is a different and more expensive solution than the one proposed above, and whether it is the one worth building is the real question this assumption puts to a human.

## Provenance

First-party observation made during the unattended maintenance pass of 2026-08-05, which reproduced the silent `## History` loss on itself. No stored evidence record exists for it, so the source is free text rather than a citation the vault cannot resolve.

## History
- 2026-08-05 merged "Being told a section was dropped is worth little to a caller who cannot restore it" into this node and deleted its file — Same belief, same wording — the original was created minutes earlier in this pass with a fabricated provenance id (`TRANSCRIPT:2026-08-05-unattended-pass`) matching no stored evidence record, reported by `ost_check` as an unresolved-citation violation. `source` is frontmatter with no setter on this surface, so re-creating with truthful free-text provenance and folding the original in is the only available repair. The merge carries the original's edge to its assumption test across.
