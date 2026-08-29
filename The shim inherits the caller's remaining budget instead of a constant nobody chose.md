---
type: Solution
source: 'agent-run:unattended-sweep-2026-08-29'
created: '2026-08-29'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[A budget that fails to reach the shim announces itself instead of silently reverting to the constant]]

**Variation dimension: automated-vs-manual. Position taken: the propagation is automated; the number itself stays a thing a person writes, in the one place they already write it.**

The composer already stated their budget: `"timeout": 400000` on the Bash call, in all six of the observed give-ups. The defect is that the number never reaches the thing that decides when to stop. So carry it. The wrapper that installs the shim on `PATH` — `examples/automation/build-pass.sh` already does the install, the `chmod` and the `PATH` export — also exports the firing's budget into the environment, and `renderWaitShim()` changes one line: `limit=${3:-300}` becomes a default that reads the environment before falling back to the constant.

**What is automated, and why it is the right half.** Only the plumbing. The composer types nothing extra — expression cost is unchanged, which matters because the module's own case for the shim's existence is that it must be no longer to write than the reflex it replaces, and the recorded margins are 14, 25 and 3 characters. This is the only one of the three candidates that fixes the mismatch without spending any of that margin.

**What stays manual, deliberately.** The budget. It is a claim about the operator's money and cadence and the shim has no business inventing it; the improvement is that the number the composer already chose becomes the number that is used, not that a better number is guessed.

**What it costs, and it is not small.** `src/loop/wait.ts` argues at length that the shim must be self-contained with nothing baked in at install time — a dependency that can go missing "fails as 'command not found' three weeks later and reads exactly like the affordance never existing." An environment variable is a softer version of that same failure and a worse one to diagnose: if the export is missing or misspelled the shim does not error, it silently reverts to 300 and the composer sees exactly today's behaviour with no signal that the mechanism did not fire. It also makes the shim behave differently in two environments, so a wait that expires in the loop and holds at a terminal is no longer a contradiction anyone can reason about. And the harness's per-call timeout is not visible to the shell today at all — somebody has to plumb it, and the plumbing is the part that can be wrong.

**Against its siblings.** It is the only candidate that costs the composer nothing, and the only one that introduces a silent failure mode. Those are the same property seen from two sides: a mechanism that asks nothing of a person is a mechanism no person notices has stopped working.

Unvalidated, ideated by an unattended pass on 2026-08-29 against the assigned dimension. **Not blind:** this surface holds no grant to run independent parallel ideators, so all three candidates under this opportunity were composed in one context by one author — the condition the blind-ideation rule exists to prevent. Read them as one author's three answers and discount their apparent distinctness accordingly.

## Definition of done

"A budget that is missing, empty or non-numeric makes the wait say so rather than quietly using 300"

```
npx vitest run test/loop/wait-budget-inheritance.test.ts
```

Four environments, and the point is the three that fail: absent, empty and non-numeric must each produce a stderr line naming the bound actually in force. Only the fourth — exported and numeric — is the happy path. Cut any of the three and the cheapest implementation passes, which is `limit=${3:-${AWAIT_LIMIT:-300}}`: correct-looking, silent, and a reproduction of the very defect this candidate exists to fix.

Assert on observed behaviour, not on the rendered source. Grepping the script for a variable name passes on a shim that reads the budget and then ignores it.

The red is a `no-spec` red — the file does not exist. It also stays red past file creation until `renderWaitShim()` reads the environment at all: today it emits `limit=${3:-300}` and consults nothing.
