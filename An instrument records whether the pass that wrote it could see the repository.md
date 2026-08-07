---
type: Solution
source: 'agent-ideation:2026-08-07-unattended-sweep'
created: '2026-08-07'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Repo sight is derivable from the surface rather than from the author]]

**The idea.** When `ost_set_instrument` records a command, it also records — from the surface's actual capabilities at that moment, not from the author's claim — whether repo sight was available. `debt` and `status` then report grounded and blind instruments as separate figures.

**Why this shape.** It does not try to make blind instruments better. It makes them *countable*, which is the thing the parent says is missing: "a grounded instrument and a guessed one are the same string in the same field." Once they are two figures, a human can decide whether 61 blind instruments is progress or laundering, and that decision is currently unavailable to them at any price.

It is also the only candidate here that leaves the backlog clearable. Both siblings slow the queue down; this one lets it keep moving while marking what it produced.

**How it compares to its siblings.**
- "An instrument naming a path that does not exist is refused" attacks the weak form directly and would have blocked most of what this pass could write. Stronger guarantee, much higher cost in blocked work.
- "A pass that cannot see the repository cannot set an instrument at all" is the same trade taken to its end: no blind instruments exist, and the backlog waits for an attended pass.

**Where it fails, stated so it can be judged.** A flag is not a fix. A tree carrying 61 instruments marked `blind` is in exactly the state the parent complains about, plus one honest column. If nothing ever consumes the flag — no gate, no report a human reads — this ships and changes nothing, and it will have made the situation *look* handled, which is worse than leaving it raw.

The flag is also only as good as the capability detection behind it. Deriving it from "the author says so" reintroduces the whole problem, so it has to come from the surface's own grant table, and that is the part worth pinning with a test.

**Cost.** A field, a source of truth for capability, and two lines in two reports. Small.

⚠️ Unvalidated. Agent-ideated by a pass that was itself blind, which is a reason to trust the observation and discount the conviction.
