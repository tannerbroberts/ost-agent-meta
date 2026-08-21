---
type: Solution
status: unvalidated
source: 'agent-ideation:2026-08-21-unattended-sweep'
created: '2026-08-21'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[An extent-equality condition evaluates without judgement against the tree alone and stops holding when either sibling's citations change]]

**Mechanism.** The product already ships a suppression ledger with typed, judgement-free conditions — `src/knowledge/suppressions.ts`, pinned by `test/ost/suppression-condition.test.ts`: `status-is`, `lane-is`, `lane-unlabelled`, `section-missing`, each a boolean over the tree alone, each reviving the item the moment the fact flips, and each refusing prose. Add one condition kind, `extents-unchanged`, over a sibling pair: it holds while the evidence extent of each named node equals the digest recorded when the verdict was entered, and stops holding when either side gains or loses a citation. An extent verdict then lives on the ledger like every other decline, is disclosed on every `ost_next_work` response under `suppressedByCondition`, and carries `by` and `reason` — and the write path stays what the ledger's own spec says it must be: the CLI's, not any agent tool's.

**Variation dimension: bought-vs-built — adopt the ledger as it is, build only the condition.** The other two candidates build new matching logic inside the extent scanner. This one reuses the product's existing answer to "an item a pass declined is suppressed until the reason it was declined stops holding" — ledger, disclosure, fail-open parsing, revival — and adds a single condition kind to it. Nothing about extents is re-invented; the extent digest is already computed by `evidenceExtents`.

**Against its siblings.** It is the only one that takes the clear off the agent surface: a sweep can still *propose* a verdict in the node's Issues, but only a human's `ost-agent suppress` (or whatever the CLI names it) silences the flag. That is slower than either sibling and is the point — the parent node records four passes adjudicating their own flags, and an agent that can both flag and clear has graded its own homework. It is also the only candidate whose clear is disclosed in the response that withheld it, rather than buried in a node's Issues.

**Where it fails.** If the human never runs the command, the flags churn exactly as before — this candidate converts an undiscoverable clear into a discoverable ask, and the vault currently holds 49 asks with no recorded answer.

⚠️ Unvalidated. Agent-ideated.
