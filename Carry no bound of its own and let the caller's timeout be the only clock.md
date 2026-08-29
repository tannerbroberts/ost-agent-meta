---
type: Solution
source: 'agent-run:unattended-sweep-2026-08-29'
created: '2026-08-29'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[Every path that can invoke the shim already carries a finite bound of its own]]

**Variation dimension: bought-vs-built. Position taken: the enforcement is adopted from the platform as-is, and the thing built here is deleted rather than improved.**

Two clocks are running and only one of them was chosen by anybody. The harness already bounds every Bash call — that is what `"timeout": 400000` on the observed calls *is* — and it already kills a call that overruns. So the shim stops keeping a second clock. `limit` and the `waited` counter come out of `renderWaitShim()`, the loop runs until the condition holds, and the only number that can stop it is the one the composer wrote. One clock, owned by the platform, chosen by the person.

**What is bought:** the bound, its enforcement, and the kill. **What is built here:** nothing. This is the only candidate of the three that removes code, and the only one where the mismatch cannot recur, because a mismatch needs two numbers.

**What it gives up, and it is the objection that should be answered before anything is built.** `DEFAULT_FOR_SECONDS`'s own docstring says the bound is deliberate and says why: the shim "exists to be written *instead of* a fixed sleep by an unattended session, and a wait that can hang forever would trade eight refusals for one wedged firing." This candidate proposes exactly the thing that comment refuses. It is defensible only if the platform's bound is always present and always finite — if some call path has no timeout, or defaults to a generous one, an unattended firing can spend its whole budget on a single wait with nobody watching. Whoever picks this up should establish that first, because a negative answer retires the candidate rather than shrinking it.

**The second cost, and it cuts against the neighbouring branch.** A harness kill is not a give-up; it is a kill. The shim's expiry path today prints the trimmed tail of the last attempt and writes `gave up after ${waited}s` to stderr, and a killed process prints neither. So this candidate makes the wait's ending *less* legible at exactly the moment the sibling opportunity beside it — "When a wait gives up, I can't tell whether it was nearly there or never going to happen" — is trying to make it more so. Picking this one forecloses that branch's whole line of work, which is a reason to sequence them together rather than to judge this candidate alone.

**Against its siblings.** It is the cheapest to build, the only one that cannot drift back out of sync, and the only one whose failure mode is a wedged unattended firing rather than a wrong number.

Unvalidated, ideated by an unattended pass on 2026-08-29 against the assigned dimension. **Not blind:** this surface holds no grant to run independent parallel ideators, so all three candidates under this opportunity were composed in one context by one author — the condition the blind-ideation rule exists to prevent. Read them as one author's three answers and discount their apparent distinctness accordingly.

## Definition of done

"Census every shim invocation path and count how many arrive with a finite bound already set"

```
npx vitest run test/loop/wait-caller-bound-census.test.ts
```

Settle this before building, because a refutation retires the candidate rather than shrinking it. The threshold is zero unbounded paths, not a majority: this candidate deletes the shim's only clock, and one unbounded call site is enough to produce the wedged unattended firing that `DEFAULT_FOR_SECONDS`'s own docstring says the bound exists to prevent. An average cannot rescue a firing that hung overnight.

Both sources matter. The corpus covers tool calls, where a `timeout` field is usually present; `examples/automation/build-pass.sh` puts the shim on `PATH`, and a script invocation runs under no harness clock at all.

The red is a `no-spec` red — the file does not exist. The data is also not being kept: `corpusCommands()` returns `{session, command}` and drops the timeout, and `WaitingCase` has no field for it. Stopping that discard is the first build step.
