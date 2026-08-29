---
type: Solution
source: 'agent-run:unattended-sweep-2026-08-28'
created: '2026-08-29'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[Expiry can be given its own exit status without breaking what already reads the shim's status]]

**Variation dimension: automated-vs-manual. Position taken: the classification is automated; the bound stays a number a person chooses.**

Today `renderWaitShim` in `src/loop/wait.ts` ends `exit "$rc"` — the condition's own status — so expiry and condition-false are the same event to any caller reading an exit code. This candidate separates them mechanically. Expiry exits with a status reserved for expiry and used by nothing else, and the give-up line reports what the wait actually saw: how many attempts it made, how long it waited, and whether the condition's output changed between the first attempt and the last. A caller that re-issues an identical wait after a give-up should be able to tell, from the exit status alone, whether it is re-issuing against something that was moving or something that was inert.

**What is automated.** Everything a machine can settle without a judgement: expiry-versus-failure, attempt count, elapsed seconds, and output-changed-or-not. All four are properties of the loop the shim already runs; none requires knowing what the caller wanted.

**What is left manual, and why that is the position rather than a shortcut.** The give-up bound itself. `DEFAULT_FOR_SECONDS` is 300 and the 2026-08-29 firing hit it four times while its own Bash call had allotted 600s — but the fix is not for the shim to infer a better number. How long a firing may spend waiting is a claim about the operator's money and cadence, and the shim has no access to either. So the bound stays an argument, and the improvement is that expiry stops being *silent about itself* rather than that the shim gets cleverer about when to stop.

**Against its siblings.** Unlike removing the wait, this works for foreign state the firing does not own — a CI check, another session's directory — which is most of the catalogued waiting cases. Unlike adopting `timeout(1)`, it keeps the shim as plain POSIX `sh` with no external dependency, which `src/loop/wait.ts` argues for at length and which is the property that lets the shim be rendered fresh into any firing's PATH.

**What it costs.** It changes an exit-code contract that something already reads. `test/loop/wait-primitive-affordance.test.ts` asserts today that a never-true condition exits with the condition's own status (`run(["exit 3", "1", "2"])` expects `3`), so that expectation has to be deliberately revised rather than incidentally broken — and any caller branching on the old behaviour has to be found first. It also adds output to a give-up line whose whole design premise was that the shim supplies terseness the caller does not have to type.

**Sharpest risk:** feasibility is cheap and the belief worth testing is whether the distinction can be added without breaking what reads the status.

Ideated by an unattended pass on 2026-08-28 against the assigned dimension. **Not blind:** this surface holds no grant to run independent parallel ideators, so all three candidates under this opportunity were composed in one context by one author — the condition the blind-ideation rule exists to prevent. Read them as one author's three answers and discount their apparent distinctness accordingly.
