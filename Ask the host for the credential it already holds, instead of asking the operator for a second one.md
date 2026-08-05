---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[The hosts this runs under expose a delegable capability, on enough of the real runs to matter]]

Where the tool runs inside a host that is already authenticated — a signed-in agent session, a logged-in CLI, an editor with an account — it asks that host to perform the action rather than asking for a key of its own. The operator's existing authentication becomes the tool's authentication, and there is no second credential to obtain, store, or rotate.

The complaint underneath this opportunity is not really about access. It is that the operator has already proved who they are, and is being asked to prove it again in a currency the tool happens to prefer.

**Compared to the alternatives.** Removes the credential question entirely rather than making it easier, and it inherits whatever protections the host already applies. It works only inside hosts that expose the capability, so a cron job or a bare shell gets nothing, and it makes the tool's reach a function of where it is running — which is the same variability the tree already complains about elsewhere.

**What would make this the wrong pick.** Borrowing the host's authority means inheriting its scope, which is usually far wider than the tool needs. An operator who would happily issue a narrow token may be much less happy to let a background pass act as their whole signed-in self.

## Test

[[Enumerate the hosts this tool runs under and check which expose a delegable capability]]

`npx vitest run test/security/host-credential-delegation.test.ts`

Green when, for every host this repository ships an entry point for, the code either resolves a host-held credential or records that the host exposes none. Bounded by what we support and true only as of the run — host capabilities change on someone else's schedule. It says nothing about whether an operator would want a run acting under a credential they did not issue for it.

## History
- 2026-08-05 unlinked [[Enumerate the hosts this tool runs under and check which expose a delegable capability]] — moved under [[The hosts this runs under expose a delegable capability, on enough of the real runs to matter]] — the belief this test measures now has a node of its own
