---
type: Opportunity
source: 'TRANSCRIPT:470cb94a-d709-43b1-85aa-dedd917ac866'
created: '2026-08-05'
evidence: observed
---
#Opportunity #unvalidated #evidence/observed

I keep paying for the same correction. When I reach for `sleep 45 && gh pr checks 17` to wait on something, the surface refuses it and tells me exactly what to do instead — use `Monitor` with an until-loop, or `run_in_background` for a command I started. The message is clear and correct. Then the session ends, and the next session I reach for `sleep 45 && gh pr checks` again.

Seven sessions across four days show the identical refusal, machine-captured: `470cb94a` (Jul 30), `4ff7b605` (Jul 29), `995b8ab1` (Jul 29), `a0eb3fd4` (Jul 29), `97546e2f` (Jul 30), `516fdfb8` (Jul 30), `87a025f8` (Jul 31). Same reflex, same guard, same wording, seven times. In `516fdfb8` the reflex outlived the refusal *within* the session too — the blocked sleep sits alongside three `TaskOutput` retries at `block: true, timeout: 600000`, which is the same impulse wearing a permitted shape.

This is narrower than the parent need, and the distinction is what makes it actionable. The parent is about knowledge not accumulating in general. This is specifically that **a correction delivered as a tool-error message has no carrier out of the session it was delivered in** — it is spoken, obeyed once, and then gone. Nothing writes it down, so nothing can hand it to the next session, and the guard ends up being the only memory in the system: it fires forever because it is the only thing that remembers.

More than one way to address it, which is what keeps this an opportunity rather than a solution: a durable per-workspace record of corrections already issued; the guard emitting a persistent note rather than only a transient message; a pre-flight that reads prior refusals before composing a call; or the surface offering the permitted form as the path of least resistance so the wrong reflex is never the cheapest thing to reach for.

Evidence class is observed behaviour of the agent's own use of its tools — captured mechanically from session transcripts, with no narrator. It grounds usability, not desirability: it says the loop is expensive, not that anyone outside this project wants it fixed.
