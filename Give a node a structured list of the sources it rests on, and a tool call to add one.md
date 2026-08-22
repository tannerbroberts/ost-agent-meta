---
type: Solution
source: 'agent-ideation:2026-08-22-unattended-sweep'
created: '2026-08-22'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A node can carry several sources without breaking the readers that assume it carries exactly one]]

**Variation dimension: what is measured — this candidate measures a declaration, where its sibling measures a mention.** The single-valued `source:` field becomes a list, and a tool call adds an id to a node that already exists. Mapping becomes a typed transition a pass performs on purpose, recorded in History like every other typed transition on this surface, rather than a side effect of how a paragraph was worded.

**Why this shape.** It fixes the root fact rather than working around it. The reason corroboration does not drain the queue is that a node can hold exactly one `source`, and every pass that appends a fifth corroborating record to a node is asserting a many-to-one relationship the data model cannot express. Making the field a list makes the model match what the tree has actually been doing since roughly its second week. It also composes with the believability ladder in a way prose cannot: `ost_set_evidence` caps a node's rung by what its source has earned, and a node resting on eight independent transcripts is a different claim from one resting on one — a distinction the current model erases and this one can carry.

**Compared to its siblings.** Strictly more expensive than "Count a source citation in a node's prose as a mapping" — a schema change, a migration for every existing node, a new tool on an already-large surface, and every reader that assumes `source` is a string. It buys unambiguity: a declared source cannot be a passing mention or a negation, so the sibling's silent-wrong-drain failure cannot occur. Against "Let a pass explicitly dispose of an evidence record it has read", it only drains records that genuinely corroborate something; records read and judged irrelevant still accumulate.

**What would make this the wrong pick.** It adds a write the agent must remember to make, so the queue drains only as well as passes are disciplined — and a pass that appends the corroboration prose and forgets the call leaves the tree in exactly today's state while believing it is done. It is also the one candidate here that touches the write boundary and the frontmatter schema, which is where this product's guards live; a migration over ~1,400 nodes is not a small blast radius for a counter.

⚠️ Unvalidated. Agent-ideated from this pass's own tool output.
