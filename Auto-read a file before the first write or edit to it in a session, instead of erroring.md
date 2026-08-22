---
type: Solution
source: 'TRANSCRIPT:0459d729-8ee3-43fc-ae1f-f05928ad84e2'
created: '2026-08-18'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Auto-reading a file before write doesn't mask the exact race condition the guard exists to catch]]
[[Editor tooling can auto-read a file transparently before a first Write Edit without weakening the guard's protection against blind overwrites]]

When Write or Edit targets a file the session has not read yet this run, have the harness perform the read itself first (transparently, no extra turn) rather than refusing with a tool_error. The guard's purpose — never clobber content the session hasn't seen — is preserved; only the burned turn and retry disappear.

**Compared to the alternatives.** This is the only candidate that removes the friction event entirely rather than helping the session recover from it faster. Its risk is the guard's whole point: if the auto-read happens invisibly, a session may still act on stale assumptions formed before that read (e.g. a plan made from a stale summary), so the fix has to genuinely feed the fresh content into the session's context, not just satisfy the guard mechanically.

## Issues
- 2026-08-17 Assumption surfaced ("Auto-reading a file before write doesn't mask the exact race condition the guard exists to catch") but its test is not created: this is a feasibility question the repository can answer (how the current guard is implemented and where the race window actually is), and this unattended sweep holds no `ost_read_repo` grant. Needs an attended pass with repo sight to write the spec-file instrument.

## Blocker discharged, and partly misrouted — repo sight held (2026-08-22 unattended sweep)

The 2026-08-17 Issues note above says this assumption is "a feasibility question the repository can answer (how the current guard is implemented and where the race window actually is)" and that the sweep lacked an `ost_read_repo` grant. This pass held the grant and read the code. **Half of that note is wrong and the other half is answered.**

**Wrong half: the guard that produced the friction is not in this repository.** The observed error is `File has not been read yet. Read it first before writing to it.` — that is Claude Code's `Write`/`Edit` precondition, belonging to the harness, and no amount of repo sight on OST-Agent will show its implementation or its race window. A future pass should stop routing this assumption at `ost_read_repo`; the question about the harness's guard is answerable only by someone with the harness source, which is the shape already on the tree as the sandbox/Monitor asks.

**Answered half: this repository holds a working existence proof that the two concerns separate cleanly** — which is what the assumption actually doubts. `src/git/read-write-hash-guard.ts` states its scope in the docstring: it "answers 'did the file drift between this read and this write', nothing more." Its mechanism is a SHA-256 of the content taken at read time and re-compared against disk immediately before the write; on mismatch it throws `DriftError` naming what moved, and it "never partially writes."

That decomposition is the point. Two distinct failures are being conflated by the friction record:

| Failure | Caught by | Would an auto-read mask it? |
|---|---|---|
| The session never read this file at all | a precondition check (the harness's) | Yes — that is the whole proposal, and it is the failure the auto-read is *supposed* to remove |
| The file changed between the read and the write | a content hash compared at write time | **No** — the baseline hash would be taken at the auto-read, and any drift after it still mismatches |

So the assumption as worded — "auto-reading a file before write doesn't mask the exact race condition the guard exists to catch" — is **supported by construction for a hash-based drift guard**, because the drift check does not care *when* the read happened, only that the content is unchanged between it and the write. It is a stale-content check, not a did-you-look check. This repo's own `Vault.editProse` runs exactly that way today.

**The caveat that keeps this from being a green light**, and it is the one this node's own prose already names: the argument holds for the *mechanical* race and says nothing about the *cognitive* one. `src/ost/plan.ts` exists precisely because the single-write guard was insufficient — a pass that reads several nodes, forms a plan, and has one of them drift partway through gets every individual write accepted while the reasoning underneath is void. A transparent auto-read makes that worse, not better: it satisfies the precondition without the content ever entering the session's reasoning, which is the "acts on stale assumptions formed before that read" risk this node's prose flags. `Plan`'s answer — widen drift from one file to everything read so far, and void the whole plan on first drift — is the shape a safe auto-read would have to take.

**Net for whoever picks this up:** the feasibility half is settled favourably from first-party code and needs no interview. What remains is a design question (does the auto-read feed content into the session's context, or merely satisfy the check?) plus the harness question, which is not this repo's to answer.

_Method: first-party `ost_read_repo` reads of `src/git/read-write-hash-guard.ts` and `src/ost/plan.ts` in full (`"truncated": false` on both). Nothing executed; the drift-window conclusion is read off the mechanism, not observed. Grounds feasibility only — it says nothing about whether an operator wants the guard softened, which is the sibling assumption and still open. No rung moved._
