---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Add the hook and check whether the commit paths a run actually uses all pass through it]]

A pre-commit check scans staged content for conflict markers and refuses the commit outright. It is a handful of lines, it has no false positives worth speaking of, and it makes the specific state described here impossible to create.

Small scope, exact fit. It does nothing about a bad merge that produced valid-looking code, but it completely prevents the case where the marker itself is what shipped — which is the case in the evidence, and the one that cost a later session a stop-and-ask.

**Compared to the alternatives.** Cheapest by a wide margin and the only one that acts at the moment of the mistake. It also catches nothing else: a resolution that dropped half a function commits cleanly and breaks just as much. Requiring the build to pass before commit would catch both; refusing to start work on a broken tree catches neither but protects the next run.

**What would make this the wrong pick.** A local hook is advisory — it lives on one machine, is skipped with a flag, and does not exist on a fresh clone. To be a guarantee rather than a habit it has to run somewhere nobody can bypass, which is a different and larger piece of work.
