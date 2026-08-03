---
type: Solution
source: 'agent:ideation-2026-08-03'
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

Rather than trying to record enough context to explain a failure, make the record executable: a recorded step can be re-run, in the directory and with the arguments it originally used, and the outcome of that re-run is appended beside the original. The operator asks "does this still fail?" and gets an answer instead of a reconstruction.

**The trade it makes:** it collapses the whole class of "looks complete, cannot be believed" records that this opportunity is about — a replay that passes tells you the failure was environmental, a replay that fails hands you a live reproduction to debug. The price is real: replay executes something, so it is only safe for steps that are side-effect-free, and deciding which those are is a judgement the tool does not have. It also cannot replay a context that no longer exists.

**How it differs from its siblings.** [[Snapshot the resolved environment, but only for the step that failed]] makes the record self-describing and readable anywhere; this makes it re-runnable but only on a machine that still resembles the original. That is the core trade-off between the two — portability of explanation versus certainty of answer.

**The strongest version of this may be the narrow one:** replay only steps the loop itself issued and already knows to be read-only, which is most of the check-shaped ones (`vitest`, `tsc`, `ost-agent check`) and none of the publishing ones.

Distinguishing assumption: that operators would trust a replay result enough to close a failure on it, rather than re-running by hand anyway — which is the very habit this opportunity says is eating the value of recording.
