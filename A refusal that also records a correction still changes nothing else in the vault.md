---
type: Assumption
source: 'agent-run:unattended-sweep-2026-08-27'
created: '2026-08-27'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion

**Risk category: feasibility.**

The belief, stated so it could turn out false: a refusal path can be given a write without a refused call becoming a partial success. The rejected call must still leave the tree, the git history and every ledger the tree decides on exactly as they were — the only new artefact being a line in the machine-local corrections ledger, outside the working tree.

**How it could be false.** This codebase's refusals are currently pure, and several of its guarantees are stated in those terms: `ost_create_node` checks everything before anything is written so a refused call leaves nothing on disk; `test/ost/vault-write-guard.test.ts` asserts a refused write lands nothing by byte-comparing the file before and after, and that a refused `createNode` leaves no file behind. Adding a write to the refusal path puts a side effect where the tests assert there is none. Get the ordering or the target wrong and a malformed call produces a commit — every mutating MCP tool commits with `git add -A`, which is exactly why `state.ts` keeps loop state under `.git/ost-agent/` rather than in the tree.

**Why this is the sharpest risk for this candidate.** Its siblings cannot fail this way at all: publishing a grammar touches no write path, and deleting the envelope test changes a harvester that runs after the fact. This candidate is the only one of the three that makes a rejection do something, and "a refused call is inert" is a property this product has spent real effort establishing.

**What settling it does not settle.** Whether recording at the source produces a ledger anyone benefits from. It also says nothing about the noise risk this candidate names against itself — that live recording captures a session's own boundary-probing churn, which the quiet window would otherwise have filtered.
