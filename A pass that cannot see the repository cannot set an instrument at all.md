---
type: Solution
source: 'agent-ideation:2026-08-07-unattended-sweep'
created: '2026-08-07'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

**The idea.** Instrument-writing is gated on repo sight. A surface without it gets the refusal instead of the write, and the test is routed to a named lane — work waiting on an attended pass — rather than being cleared blind.

**Why this shape.** It is the only candidate that makes the guarantee unconditional. The other two produce a tree in which some instruments are grounded and some are not, and rely on a downstream reader caring about the difference. This produces a tree in which every instrument was written by something that had read the code, and the price of that is paid visibly, as a backlog with a name on it.

It also answers a question the other two dodge: what a blind pass should *do* with `solutionsMissingInstruments`. Under the siblings, the answer is "write instruments anyway, marked or checked". Under this one, the answer is "nothing, and say so", which is what the last three passes have done by hand each time and had to re-reason from scratch.

**How it compares to its siblings.**
- "An instrument records whether the pass that wrote it could see the repository" is the observe-only floor; this is the ceiling. Both could ship, in that order.
- "An instrument naming a spec path that does not exist is refused" catches the weak artefact even from a sighted author, which this does not — a pass with repo sight can still write a lazy path under this rule.

**Where it fails, stated so it can be judged.** This trades throughput for groundedness, and the exchange rate is unknown. 61 solutions currently wait on an instrument; under this rule an unattended fleet contributes zero of them, and whether an operator prefers 61 honest gaps to 61 guessed commands is a question about what they want, not about the code. That is the assumption beneath this node and it is not one a spec can settle.

The blunter risk: gating on capability means the capability becomes the thing to acquire, and the cheapest way to acquire it is to widen a grant. A rule that makes blindness expensive is a rule that argues for handing an unattended loop repository access, which is a different safety conversation entirely and should be had deliberately rather than as a consequence.

**Cost.** A capability check and a lane. Small to build, large to live with.

⚠️ Unvalidated. Agent-ideated.
