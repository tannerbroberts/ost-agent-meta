---
type: Solution
source: 'agent-run:unattended-sweep-2026-08-29'
created: '2026-08-29'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[A verdict tool restricted to the humans-required label cannot move any test into a lane compute may run]]
[[The operator will accept an unattended pass moving work toward people on its own authority]]

**Variation dimension: who-does-the-work. Position taken: the agent carries it — and only ever in one direction.**

Grant `ost_flag_humans_required` to the unattended surface. The parent node records that three of the seven entries it sampled name the same blocker in the same words: the label that would take them off the list is set by `ost-agent lane --set`, and the one tool that could record the verdict is withheld from the firing that keeps re-deriving it.

**Why this direction is safe where the general case is not.** `src/knowledge/lanes.ts` makes `computeMayRun` true for exactly one lane and fails closed on everything else, and `CAUTIOUS_LANE` is `humans-required` — the module already encodes that erring toward a person is the cheap error. A tool that can only *add* the humans-required label can only ever shrink what compute may run. That is the opposite of the self-dismissal risk `dispositions.ts` calls "the highest-risk write on the surface": this write costs the agent work rather than saving it, so the party writing it is not the party whose budget it serves.

**What is deliberately NOT granted.** The permissive direction — declaring a test compute-only — stays a human's `ost-agent lane --set`. So does `no-genuine-need`. An agent that could label its own tests runnable would be clearing its own gate.

**Contrast with the siblings.** The sibling that splits the report changes only what is displayed and leaves every verdict with a person; the sibling that adopts the disposition ledger routes the verdict through a human's CLI command that already ships. This one is the only candidate that puts the judgement itself in the agent's hands, which is its whole risk and its whole appeal.

**What it does not fix.** An entry that is parked for a reason *other* than needing people — the mechanism already ships, the deciding artefact lives outside this repo, a human owes it an (a)/(b) decision — has no humans-required verdict to record, and this candidate leaves all of those on the list exactly as they are. On the parent's own sample that is four of seven.

⚠️ Unvalidated, agent-ideated. No operator has said they want an unattended pass moving work toward people on its own authority.
