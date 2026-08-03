---
type: Opportunity
status: unvalidated
source: 'INBOX:2026-07-24-friction-the-ost-vault-for-this-repo-is-not-discoverable-.md'
created: '2026-07-25'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion
[[A pointer file in the project root that names its vault, read by anything that opens the repo]]
[[The vault lives inside the repository it maps, so there is nothing to point at]]
[[An agent-side convention that finds the vault by searching upward, so nothing needs recording]]

**The need (operator's voice):** "Finding this repo's vault took six exploratory commands and a guess between four candidate directories in $HOME. Nothing in the repo, its config, or its docs says where its own discovery tree lives."

**Why it matters:** every session that wants to run a pass, check status, or maintain the tree first has to rediscover the vault — a cost paid by every agent and every human, every time. Observed at the moment of friction by the builder loop, 2026-07-24; independently re-observed by a later session (a memory note now serves as the missing pointer, which is a workaround, not a fix).

**Litmus (more than one way?):** yes — a repo-side config key, a well-known dotfile (.ost-vault), vault registry in user config, or `ost-agent status` discovering by search are all distinct answers.

**Solution ideation deferred:** dogfood-lane need; expand when prioritized (see root Prioritization).

## History
- 2026-07-24 evidence: (none) → observed — labeled at creation intent; ost_create_node@0.1.3 silently dropped the evidence input
- 2026-08-01 evidence: observed → assertion — demoted by the fifteenth pass — B3's rung-unearned guard (v0.23.0-line) shipped after this node was authored; its source is not a TRANSCRIPT: recording, so 'observed' was unearned. Demotion only, per rungs.ts's own remedy.
