---
type: Solution
source: 'agent-ideation:2026-08-07-unattended-sweep'
created: '2026-08-07'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Friction shapes are separable by a mechanical signature]]

**The idea.** At ingest, friction events are reduced to a signature — tool name plus the normalised refusal text, with paths and ids stripped. Items sharing a signature arrive in the queue as one entry carrying the number of times it was seen and the sessions it came from.

**Why this shape.** It asserts nothing about needs. It only says that two byte-similar refusals from the same tool are the same *observation*, which is a mechanical claim a fixture can check. The parent records that the 76-item backlog is "the same four needs observed 76 times"; this is the version of that finding a machine can reach without deciding what a need is.

**How it compares to its siblings.**
- "An evidence item can be filed as corroboration of a node that already exists" puts the frequency on the opportunity, where a reader will actually meet it. This puts it on the queue entry, where it is visible only while unmapped. Weaker placement, far weaker claim.
- "An unmapped item ages out of the queue into a digest" hides volume; this compresses it. Compression keeps the signal, so it is strictly better on that axis and strictly more code.

**Where it fails, stated so it can be judged.** Normalisation is where this dies. Strip too little and 76 items stay 76 because each carries a different session id and path; strip too much and two genuinely different refusals — a permission denial for `ost_check` and one for `ost_read_repo` — collapse into one entry, and the tree loses the fact that two distinct capabilities were withheld. There is no setting that is obviously right, and the failure is silent in the over-stripping direction.

It also does not clear the backlog. Four grouped items are still four unmapped items, and the parent's complaint — that corroboration has nowhere to go — is untouched.

**Cost.** A normaliser and a grouping key at ingest, plus fixtures built from the corpus's real strings.

⚠️ Unvalidated. Agent-ideated.
