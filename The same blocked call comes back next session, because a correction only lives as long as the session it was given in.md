---
type: Opportunity
source: 'TRANSCRIPT:470cb94a-d709-43b1-85aa-dedd917ac866'
created: '2026-08-05'
evidence: observed
authorship: machine
---
#Opportunity #unvalidated #evidence/observed
[[A corrections ledger in the workspace that every session reads before it composes]]
[[The guard turns each correction into a workspace constraint, so the wrong call stops being expressible]]
[[Offer the permitted form at the moment of reach, so the wrong reflex is never the cheapest thing to write]]

I keep paying for the same correction. When I reach for `sleep 45 && gh pr checks 17` to wait on something, the surface refuses it and tells me exactly what to do instead — use `Monitor` with an until-loop, or `run_in_background` for a command I started. The message is clear and correct. Then the session ends, and the next session I reach for `sleep 45 && gh pr checks` again.

Seven sessions across four days show the identical refusal, machine-captured: `470cb94a` (Jul 30), `4ff7b605` (Jul 29), `995b8ab1` (Jul 29), `a0eb3fd4` (Jul 29), `97546e2f` (Jul 30), `516fdfb8` (Jul 30), `87a025f8` (Jul 31). Same reflex, same guard, same wording, seven times. In `516fdfb8` the reflex outlived the refusal *within* the session too — the blocked sleep sits alongside three `TaskOutput` retries at `block: true, timeout: 600000`, which is the same impulse wearing a permitted shape.

This is narrower than the parent need, and the distinction is what makes it actionable. The parent is about knowledge not accumulating in general. This is specifically that **a correction delivered as a tool-error message has no carrier out of the session it was delivered in** — it is spoken, obeyed once, and then gone. Nothing writes it down, so nothing can hand it to the next session, and the guard ends up being the only memory in the system: it fires forever because it is the only thing that remembers.

More than one way to address it, which is what keeps this an opportunity rather than a solution: a durable per-workspace record of corrections already issued; the guard emitting a persistent note rather than only a transient message; a pre-flight that reads prior refusals before composing a call; or the surface offering the permitted form as the path of least resistance so the wrong reflex is never the cheapest thing to reach for.

Evidence class is observed behaviour of the agent's own use of its tools — captured mechanically from session transcripts, with no narrator. It grounds usability, not desirability: it says the loop is expensive, not that anyone outside this project wants it fixed.

## 2026-10-09: a ledger now exists, and the refusal it does not carry came back in this firing

The corrections ledger is now live. This firing's prompt opened with "CORRECTIONS ALREADY ISSUED IN THIS WORKSPACE", and it carries the sleep-polling correction this node was written about ("refused 10 time(s) across 10 sessions") plus "Bash … is not enabled". It does **not** carry a third recurring refusal: a harness `Grep`/`Glob` aimed at the product repo's path (`/Users/tanner/dev/OST-Agent/src`) is denied with "Claude requested permissions to read from …, but you haven't granted it yet." `ost_read_repo` reads the same files and is permitted on this surface.

Sessions with that refusal, read in full this firing: `030e5db3` (Glob on `…/OST-Agent/src`), `08103a74` (Glob on `…/OST-Agent`, 2026-09-22), `07141404` (Grep on `…/OST-Agent/src`, 2026-10-07). Also `015d5a7e` (Grep on `/dev/null`, 2026-10-05), a different path that gets the same denial. **This firing then made the same call** (Grep on `…/OST-Agent/src`), with the ledger in its prompt, and was refused the same way.

**What this adds to the node.** A ledger that someone fills in has the same blind spot one level up. It carries the corrections it was given and has no entry for a refusal that never named an alternative. A permission denial says only "not granted". It never says "use `ost_read_repo`". So nothing in it could be turned into a ledger entry, even though it recurs as often as the refusals the ledger does record. That bears on the three candidates below. One that records only refusals which already name their permitted form would not have caught this one.

_Method: four evidence bodies read via `ost_next_work({evidence})`, plus this firing's own refused call. Observed behaviour of this agent's surface. It grounds usability, not desirability. These records stay in `unmappedEvidence` because only a `source:` field drains that queue (see "I map evidence the way the method says — onto an existing node — and the queue counts it as untouched"). Nothing was executed, no rung moved, and no instrument was set. `ost_check` is withheld on this surface, so this write has not been verified by the invariant checker._
