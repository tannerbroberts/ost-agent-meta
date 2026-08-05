---
type: Solution
status: unvalidated
source: 'agent-ideation:autonomous-loop-2026-07-25-pass5'
created: '2026-07-25'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Refusing an unfixed threshold blocks few enough filings to be a guard rather than a wall]]

**The idea.** `ost-agent result` refuses a filing when the test's pre-commitment is
not a commitment — the same shape as its existing refusals for a blank `--by` and a
blank `--uncovered`, and for the same reason. A result recorded against "decide a
threshold before starting" cannot be refuted, and an irrefutable result is the thing
this whole product exists to keep out of the tree.

**Approach.** Reuse the classification from
"Flag a threshold that is still an instruction to choose one" at the write
boundary rather than the read one. The refusal names the node and prints what it
found, so fixing it is one edit.

**How it differs from its siblings.** The flag informs; this one stops. That is the
whole difference and it is not small: refusal is the only version that cannot be
skimmed past.

**The risk, stated plainly, and it is the one that should decide this.** v0.8.0 added
a required argument to `ost-agent result` and thereby invalidated three paste-ready
verdict commands that a human had already not run for four briefings — the loop made
its operator's waiting task harder, and the briefing that shipped it said so. This
would be the *second* required-field addition to the same command, aimed at the same
person, who is still not running it. An agent that keeps hardening the one command
its operator is already avoiding should be read as optimising the wrong thing.

**Trade-off.** Correctness at the write boundary versus the risk of making the last
mile of the human's job heavier again. The honest sequencing is: do not build this
until somebody has actually recorded a result under the current rules.

**Contrast worth keeping.** If the classification is wrong at the edges — and the
parent opportunity says it will be — a wrong flag costs a glance and a wrong refusal
costs the whole recording.

⚠️ Unvalidated. Proposed by an agent. Deliberately proposed *after* the report
version, and it should stay behind it.

## History
- 2026-08-05 unlinked "Replay all existing tests to count how many a refusal would have blocked" — moved under "Refusing an unfixed threshold blocks few enough filings to be a guard rather than a wall" — the belief this test measures now has a node of its own

## Proving this

"Replay all existing tests to count how many a refusal would have blocked"

```
npx vitest run test/ost/unfixed-threshold-refusal-census.test.ts
```

Red today: the unfixed-threshold classifier is wired only to the read boundary (the flag), so no code path applies it to a result filing or reports how many filings it would have blocked. Green when the census exists.

**What a green run would not settle, and here it is the deciding question.** The census answers "is this a guard or a wall" — a count. It says nothing about the risk this node names as the one that should decide it: that this would be the second required field added to the one command the operator is already not running. That is a question about a person's willingness, and this node's own honest sequencing — do not build until somebody has recorded a result under the current rules — is not something an exit code can enforce.
