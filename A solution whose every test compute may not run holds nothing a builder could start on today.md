---
type: Assumption
source: 'agent-ideation:2026-08-30-unattended-sweep'
created: '2026-08-30'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion

**Risk category: feasibility.**

The belief, stated so it could be false: dropping these solutions from `solutionsMissingInstruments` loses no work anybody could have acted on, because a lane `computeMayRun` refuses means no command will ever be run against that test by the loop, so the bucket's own purpose — hand a builder a definition of done — cannot be served by the entry however long it is listed.

**How it could turn out false.** A solution can carry several tests. If even one of them is in a runnable lane while its siblings are not, the solution has a live path to a builder and a filter keyed on "every test" must not drop it — but a filter written carelessly, keyed on "any test", would. The failure is silent: the solution vanishes and the one runnable test beneath it goes with it.

It could also be false in the other direction, on a tree where lanes are absent rather than set. An unlabelled test falls to the cautious lane by `computeMayRun`'s fail-closed rule, so a filter reading that rule would drop every solution whose tests were simply never labelled — which is most of a tree written before lanes existed, and is a very different act from honouring a decision somebody made.
