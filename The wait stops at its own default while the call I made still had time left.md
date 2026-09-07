---
type: Opportunity
source: 'TRANSCRIPT:029e4edb-7a41-4ef1-9851-dbe3a4f986b1'
created: '2026-08-29'
evidence: observed
authorship: machine
---
#Opportunity #unvalidated #evidence/observed
[[Show the bound in the affordance so the composer names their own number every time]]
[[The shim inherits the caller's remaining budget instead of a constant nobody chose]]
[[Carry no bound of its own and let the caller's timeout be the only clock]]

**The need, in the composer's voice:** "I told the call how long it had. The helper stopped somewhere else, and never told me the number it was actually using."

**What was observed, first-party.** Session `029e4edb-7a41-4ef1-9851-dbe3a4f986b1` (2026-08-29, unattended, nobody watching) produced 15 friction events, and **six of them are the same line**: `await: gave up after 300s; the condition still exits 1.` The three `retry` events in the same record show what the composer did about it — re-issued the identical wait, twice for `/tmp/final-run.txt` and once for `/tmp/full-suite.txt`. The firing spent the better part of half an hour re-arming a wait by hand.

**Why that is a need and not just a slow suite.** Every one of those Bash calls carried `"timeout": 400000`. The composer had a budget in mind, wrote it down, and it was 400 seconds. The helper gave up at 300 — `DEFAULT_FOR_SECONDS = 300` in `src/loop/wait.ts` — and the two numbers never met. There is no defect in either number on its own. The gap is that the composer stated a bound in the one place they were shown how to state one, and the thing that actually decided when to stop was a different number they were never shown.

**Why the composer did not simply pass a longer bound, read off the product's own code.** The shim's usage line is `await '<condition>' [seconds-between-attempts] [give-up-seconds]` — the bound is the *third* positional argument, so raising it means also naming a retry interval you had no opinion about. And `renderWaitAffordance()`, which is the text that reaches a session at the moment it is refused, emits three example lines and **every one of them is the bare `await '<condition>'` form**. The affordance teaches exactly the form that cannot express a bound. A composer following the guidance verbatim gets the default and no hint the default exists.

**How this differs from the sibling beside it.** "When a wait gives up, I can't tell whether it was nearly there or never going to happen" is about the *content of the verdict* — expiry versus condition-false, moving versus inert. This node is about *whose number decided the verdict*. They are distinct under Torres's test: a wait that reported expiry as its own outcome with a full liveness account would still have stopped at 300s against a 400s budget, and a wait that honoured the caller's bound would still say nothing about whether the condition was moving. A solution addresses one without addressing the other.

**Litmus test (more than one way to address this?):** Yes, and they are not variations of each other — default the bound to the caller's remaining budget rather than to a constant; make the bound a named argument instead of a third positional behind one nobody wants to set; have the affordance line show the bound so the number is visible at composition time; have the shim announce on first attempt which bound it will use; let expiry re-arm within the caller's budget instead of exiting. Passes.

**Evidence rung: `observed`.** Mechanically captured from this product's own session transcript, and the mechanism half is a first-party read of `src/loop/wait.ts`. It grounds usability, not desirability: it is the agent's own use of the product, not an outside party's demand. No test was run and no result is recorded.

**For a human to review:** whether this belongs as a sibling of the give-up-verdict node or beneath it. This pass judged them siblings on the reasoning above, and placed this node under the category rather than under the sibling so the judgement is visible rather than buried in an edge.

## 2026-09-07 — the same gap observed again, nine days later, wider and costlier

Four lines. A second first-party instance of the mechanism this node already describes, not a new claim.

**What was observed.** Session `920a768c-5335-44d1-8c50-97a23bd46517` (2026-09-07, unattended, nobody watching), captured this firing and read in full: 16 friction events, of which **eight are the identical line** `await: gave up after 300s; the condition still exits 1.` The three `retry` events show the same hand-re-arming this node already records — the composer re-issued the same wait on `/tmp/full-suite.txt` once and on `/tmp/full-suite2.txt` three times, waiting on a `vitest exit=` marker that never appeared.

**The gap is wider than the instance this node was written from.** Every one of those Bash calls carried `"timeout": 600000`. On 2026-08-29 the stated budget was 400s against the helper's 300s constant; here it is 600s against the same 300s. The composer stated a bound twice as long as the one that actually decided the verdict, and was shown neither number. That is the node's claim — "whose number decided the verdict" — reproduced at a larger ratio rather than restated.

**Why this is worth one section and not a new node.** It changes no claim here and proposes no solution. What it adds is that the need is standing rather than a single session's bad luck: two unattended firings, nine days apart, on different suites, each burning roughly half an hour re-arming a wait by hand, with the stated-versus-actual bound diverging further in the later one. The three solutions already hanging beneath this node are untouched and none was ideated or re-ranked by this pass.

**Limits.** One session record, read first-party through `ost_next_work({evidence})`; the 300s figure is this node's own prior read of `src/loop/wait.ts` and was not re-read this pass. It grounds usability, not desirability — the agent's own use of the product, not an outside party's demand. Nothing was executed, no result recorded, no rung moved, no status changed.
