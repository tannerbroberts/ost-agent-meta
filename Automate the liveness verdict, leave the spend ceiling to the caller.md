---
type: Solution
source: 'agent-run:unattended-sweep-2026-08-28'
created: '2026-08-29'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion

**Variation dimension: automated-vs-manual. Position taken: the verdict is automated, the budget stays manual.**

Split the wait into the part a machine can decide and the part it must not. Automated: whether the watched work is still alive. The wait stops returning a two-valued answer (condition true / gave up) and returns three — *done*, *still running*, *gone* — by checking the process rather than only the marker it was told to grep for. Manual: how long the caller is willing to spend. The ceiling becomes an argument the waiter declares, because how much compute a wait may burn is a spend decision and this product puts spend decisions with the operator everywhere else.

**Why the split falls there.** Liveness is a fact — a PID exists or it does not — and nothing is decided by reporting it. Duration is not a fact; it is a bet about how much a result is worth, and a fixed 300s baked into a helper is that bet made once, by whoever wrote the helper, for every caller forever. The observed session shows both halves failing at once: it did not know the suite was alive, *and* it tried to say how long it wanted by setting `timeout: 500000` on the tool call — which had no effect, because the cap belonged to the helper. The caller reached for exactly this affordance and it was not connected to anything.

**What it costs.** It is the most machinery of the three. Liveness is easy for a local child process and progressively harder for a detached process, a container, or work on another machine — and a wait that reports *still running* by a weak check is worse than one that stays silent, because it authorises further spend on a false positive. It also does not remove the guess about *what completion looks like*: the caller still supplies a condition, and "grep for `Test Files` in the output file" can be wrong about a job that is alive, finished, and wrote a different string.

**Against its siblings.** The delete-the-wait sibling removes the poll for harness-tracked work; this one is the answer for everything left over, which is the slice that sibling explicitly does not cover. Against the adopt-a-primitive sibling: this is the only one of the three that yields a *third* outcome. Off-the-shelf waits are overwhelmingly two-valued — they tell you the thing finished or that you stopped waiting — so adopting one inherits the exact ambiguity this candidate exists to remove.

**What would make this the wrong pick.** If expiry turns out to be rare once the bound is settable at all, then the liveness verdict is machinery built for a case that stopped happening, and the cheap fix — make the number an argument, change nothing else — was the whole answer. The observed evidence cannot distinguish these: nine expiries against one fixed cap tell us the cap was wrong and tell us nothing about how often a correctly-budgeted wait would still expire.

Unvalidated, and ideated by an unattended pass. Not blind — see the note on the sibling candidate "Delete the wait: let harness-tracked work announce its own completion instead of being polled"; all three were composed in one context by one author.
