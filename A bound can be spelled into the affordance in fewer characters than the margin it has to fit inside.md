---
type: Assumption
source: 'agent-run:unattended-sweep-2026-08-29'
created: '2026-08-29'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion

**Risk category: feasibility**, in the specific sense this module has made feasibility mean — not "can it be coded" but "can it be written by a composer in a hurry."

**The belief, stated so it can be false:** there is a spelling of an explicit bound short enough that the permitted form still costs no more to write than the blocked form it replaces, on every recorded waiting case.

**Why it is probably false, by arithmetic the repository already pins.** `test/loop/wait-primitive-affordance.test.ts` asserts `expect(margins).toEqual([14, 25, 3])` — the character headroom the shim has over the blocked reflex on `ci-check`, `started-task` and `condition` respectively. The obvious spelling, two trailing positionals as ` 5 400`, is six characters. Six is more than three. On the `condition` case the affordance would become more expensive to write than `sleep 240; …`, and `src/loop/wait.ts` says exactly what that makes it: "A primitive nobody can reach in fewer keystrokes than `sleep` is not an affordance, it is a preference."

**Why it is still worth testing rather than conceding.** The six-character figure assumes the bound must travel with an interval nobody wants to set. It need not: a single trailing number read as the bound, a suffix on the condition, or dropping the interval argument entirely are all cheaper spellings, and the margin only has to be beaten on the worst case rather than on average. The assumption is about whether *any* spelling fits, not whether the obvious one does.

**What turns on it.** If no spelling fits, this candidate cannot be built as stated and the choice is between abandoning the expression-cost criterion — which would require re-arguing the whole basis on which the shim was justified — and picking a sibling that costs the composer nothing.

**What it does not settle.** Nothing about whether a composer shown a bound would actually set a sensible one, which is a question about people and not about characters.
