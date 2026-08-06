---
type: Solution
source: 'agent-run:autonomous-loop-2026-08-06'
created: '2026-08-06'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A command's exit code at write time distinguishes unbuilt behaviour from a broken environment]]

**The idea.** Move the guard from the queue to the write boundary. `ost_set_instrument` runs the command it is handed before accepting it, and refuses when it exits 0 — with a message that says the solution appears to be already built and points at the status field. The queue can go on listing whatever it likes; the wrong answer simply cannot land.

**Why this one.** Both siblings key off `status: shipped`, which is prose-derived and unverified. This one keys off the repository, which is the thing everyone is actually arguing about. The tool already asserts the red-now property in its own tool description and in the ruleset — "an instrument that already passes cannot fail, so it measures nothing" — and then does not check it, which means the single load-bearing property of every instrument in this tree is currently enforced by the honour of the agent writing it. That is the same class of gap as an agent grading its own homework, and this tree has a whole bucket for that.

**How it compares to its siblings.**
- Both siblings fix the *symptom this pass observed* (noise in one list) and neither can catch a green instrument written against an unshipped solution — which is the more dangerous case, because it produces a node that looks tested and is not. This one catches every case and does not care about status at all.
- It is the only one that would have caught what a less careful pass would have done here. This pass declined to write instruments for the five shipped nodes by reasoning about them; nothing would have stopped it writing them.

**Where this fails, stated so it can be judged rather than assumed.** It executes code as part of a write, which is a large new capability on a surface deliberately built without a shell tool — the tree's own "Append-only tool surface with no delete or shell tool" solution argues the opposite direction, and this is in real tension with it. Execution is also slow, non-deterministic and environment-dependent: a spec that fails because a dependency is missing reads as a valid red instrument, so the guard would happily accept a command that is red for a reason nobody wants. And it cannot run at all on a surface with no execution grant, which is exactly the surface this pass ran on — so it would have to degrade to accepting unverified instruments, which is where the tool already is.

**Cost.** The largest of the three by a wide margin: an execution path, a timeout policy, a sandbox question, and a decision about what to do when the command cannot be run.

⚠️ Unvalidated. Proposed by the agent whose unchecked writes it is designed to refuse; that is a reason to take the diagnosis seriously and to distrust the enthusiasm.

## Definition of done

"Feed the guard three reds and one green and require it to sort them"

```
npx vitest run test/mcp/instrument-red-now-guard.test.ts
```

Red today: nothing executes a candidate command — `ost_set_instrument` checks the command's shape and takes red-now on the author's word. Green when the guard classifies all four planted exit codes correctly.

Before building this, settle the prior question it raises: adding command execution to a write path contradicts "Append-only tool surface with no delete or shell tool", and that is a decision about what this product is willing to be. A passing spec does not authorise it.

The test title is quoted rather than linked because it is already wikilinked once by its parent Assumption, and a second link would fail `check`'s single-backlink rule.
