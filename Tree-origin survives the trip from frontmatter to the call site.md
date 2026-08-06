---
type: Assumption
status: unvalidated
source: 'TRANSCRIPT:6e66c934-24d8-4200-b6f2-7af23002c478'
created: '2026-08-06'
evidence: observed
---
#Assumption #unvalidated #evidence/observed
[[Replay the two titles that broke ripgrep through every path that reaches a command]]

**Feasibility.** The scheme needs "this came from the tree" to be a property of the value at the moment it reaches a command, not a fact about its history that a reader could reconstruct.

Stated so it can be false: a wrapper placed on a title when it is read out of frontmatter is still on it three function calls later, when the string is formatted into a search. It is false at the first boundary that unwraps for convenience — a log line, a comparison, a template that needs a plain string, an equality check against a literal. Each of those is a reasonable thing to write and each produces a bare string that has lost its provenance and looks exactly like one a person typed.

The failure is silent and asymmetric, which is what makes it worth testing rather than reasoning about. A hole does not announce itself; it sits unexercised until a title with a brace in it happens to travel that particular path, at which point the failure is identical to having no scheme at all — except that everyone now believes there is one. That is strictly worse than the status quo, because the current state at least produces a visible parse error rather than a false sense of coverage.

Where it could be true: if the unwrap is a named call that is itself the quoting step, so the only way to get a usable string is to have chosen a destination for it. Then provenance does not need to survive — it is consumed exactly once, at the boundary where it matters, and there is no bare form in circulation to lose.

That reframing is probably the right design and it is not what the parent solution's title describes. The test below is written to distinguish the two, because "route arguments through a quoter" and "there is no unquoted form" are different products and only the second one holds.
