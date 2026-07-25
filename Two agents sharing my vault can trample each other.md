---
type: Opportunity
status: unvalidated
evidence: observed
source: 'INBOX:2026-07-24-friction-two-loops-share-one-git-managed-vault-with-no-wr.md'
created: '2026-07-25'
---
#Opportunity #unvalidated #evidence/observed

**The need (operator's voice):** "I had a thinker loop and a builder loop working the same git vault. Nothing told either whose turn it was — the builder had to check for a clean tree and hope, and would have had to back off mid-work if the thinker were mid-commit."

**Why it matters:** unattended operation (the parent need) assumes the processes writing the vault coordinate. There is no lease, no queue, no write contract — so adding a second loop converts 'walk away safely' into 'walk away and hope the writers interleave kindly'. Observed at the moment of friction by the builder loop, 2026-07-24.

**Litmus (more than one way?):** yes — a lock/lease file, a write queue, single-writer-per-vault convention, or serializing loops through one scheduler are all distinct answers.

**Solution ideation deferred:** dogfood-lane need; expand when prioritized (see root Prioritization).

## History
- 2026-07-24 evidence: (none) → observed — labeled at creation intent; ost_create_node@0.1.3 silently dropped the evidence input
