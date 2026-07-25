---
type: Opportunity
status: unvalidated
evidence: observed
source: 'INBOX:2026-07-24-friction-the-ost-vault-for-this-repo-is-not-discoverable-.md'
created: '2026-07-25'
---
#Opportunity #unvalidated #evidence/observed

**The need (operator's voice):** "Finding this repo's vault took six exploratory commands and a guess between four candidate directories in $HOME. Nothing in the repo, its config, or its docs says where its own discovery tree lives."

**Why it matters:** every session that wants to run a pass, check status, or maintain the tree first has to rediscover the vault — a cost paid by every agent and every human, every time. Observed at the moment of friction by the builder loop, 2026-07-24; independently re-observed by a later session (a memory note now serves as the missing pointer, which is a workaround, not a fix).

**Litmus (more than one way?):** yes — a repo-side config key, a well-known dotfile (.ost-vault), vault registry in user config, or `ost-agent status` discovering by search are all distinct answers.

**Solution ideation deferred:** dogfood-lane need; expand when prioritized (see root Prioritization).

## History
- 2026-07-24 evidence: (none) → observed — labeled at creation intent; ost_create_node@0.1.3 silently dropped the evidence input
