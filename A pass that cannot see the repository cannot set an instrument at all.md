---
type: Solution
source: 'agent-ideation:2026-08-07-unattended-sweep'
created: '2026-08-07'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Operators would rather have honest gaps than guessed commands]]

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

## Definition of done

"Five operators choose between sixty-one weak instruments and sixty-one blanks"

There is deliberately **no command** here. This solution's risk is not mechanical — it trades throughput for groundedness, and whether that trade is wanted is a preference the repository cannot hold. The test names five operators who run an unattended agent overnight and pay for the compute, and it is created human-required rather than left as prose nobody is assigned to.

A builder should not start this one until that result exists: building it and being wrong costs the whole unattended instrument backlog.

## Issues
- 2026-08-07 2026-08-07 A human-required test still reads as instrument debt — observed on this node, minutes after it was created, and it is a defect in the queue rather than in this node.

This solution's only assumption test is "Five operators choose between sixty-one weak instruments and sixty-one blanks", created with `humansRequired` because the measurement is an operator's preference and no command can hold one. That is the correct, sanctioned outcome for a test of this kind. The very next `ost_next_work` call listed this solution in `solutionsMissingInstruments` — the bucket whose instruction is "declare an `instrument:` (one spec file that fails today and passes when the solution is built)".

So the queue is asking for a command that should never exist. A pass that complies writes a spec for a question about human preference, which is the laundering the human-required lane was built to prevent; a pass that declines leaves the entry outstanding and meets it again next pass. Neither is a good outcome and the surface offers no third one, since `ost_flag_humans_required` is withheld here and would in any case refuse a test whose lane is already declared.

Scope, measured rather than guessed: `solutionsMissingInstruments` went from 61 to 62 across this pass, and this node is the increment. The other 61 have not been checked for the same shape, so the true size of the miscount is unknown and is worth counting before anything is built.

This is a sibling of "The queue sends me to ideate under a heading that already has thirty solutions under it" — same family, different bucket: the queue reports a gap that is not a gap and instructs the wrong work. It is filed here as an annotation rather than as a new Opportunity because whether it is a distinct need or a second instance of that one is a judgement about the opportunity space, and an unattended pass that has already created four opportunities today should not also decide that. For a human: if it is distinct, it wants a node of its own under the same bucket; if it is the same need, that node's three candidate solutions should each be checked for whether they cover this case, and none of them currently does.
