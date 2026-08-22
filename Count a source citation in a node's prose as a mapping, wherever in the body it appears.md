---
type: Solution
source: 'agent-ideation:2026-08-22-unattended-sweep'
created: '2026-08-22'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[The evidence ids already sitting in node prose are enough to drain most of the queue, and are not mostly negations]]

**Variation dimension: where the fact lives — this candidate reads it from the body, not the frontmatter.** The mapping predicate stops looking only at `source:` and scans each node's whole text for evidence ids. A record named anywhere in any node — a `_Source:_` line, a corroboration table, a dated finding — counts as mapped.

**Why this shape.** It requires no migration, no new tool and no new field, and it makes the queue agree with what passes have *already been doing for weeks*: the citations are all there, in the prose, correctly formatted, in most cases with an explicit `_Source: TRANSCRIPT:… — observed behavior…_` footer. The information the queue needs already exists on disk; nothing has to be written, only read. It would drain a large share of the 363 on the first run with no human act and no change to how passes work.

**Compared to its siblings.** "Give a node a structured list of sources it rests on" makes mapping a declared fact and this makes it an observed one — cheaper, and weaker for exactly that reason. "Let a pass explicitly dispose of an evidence record it has read" drains records that were read and judged *not* to reveal a need, which this cannot see at all: a record nobody cited stays listed forever under this candidate even if six passes read it and correctly decided it was noise.

**What would make this the wrong pick, stated so it can be judged.** Prose is unstructured, so the scan cannot tell *how* an id is being used. A node saying "this is **not** the same failure as `TRANSCRIPT:abc`" would drain `abc` on a mention that argues the opposite. That is not hypothetical in this vault — nodes here routinely cite records to distinguish them from neighbouring ones. The failure is also silent and one-directional: a wrongly-drained record is invisible from then on, whereas the status quo's error (never draining) at least stays loud. Anyone building this should decide whether a bare mention is enough or whether it must sit under a recognised heading.

⚠️ Unvalidated. Agent-ideated from this pass's own tool output.
