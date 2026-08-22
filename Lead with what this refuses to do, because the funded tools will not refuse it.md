---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Buyers treat refusals as trustworthiness rather than as the product being worse]]
[[Every refusal the positioning names is bound to a live guard, so the copy cannot outrun the code]]

Stop competing on generating trees, which is table stakes and which the funded tools do with more people. Position on the refusals: a tool that cannot mark its own output validated, cannot invent the outcome, cannot record a test result it did not watch a human run, and caps every claim at the rung its source actually earned. What is being sold is a discovery record a sceptic will believe, and the mechanism is what the tool is structurally unable to do.

The wager is that generated discovery artefacts have a credibility problem, and that a vendor whose product is enthusiastic and unfalsifiable cannot solve it by adding a confidence score.

**Compared to the alternatives.** This differentiates on something a funded competitor genuinely cannot copy quickly, because copying it means removing capability their existing customers already have. Publishing a head-to-head diff would be more concrete but invites comparison on their ground; competing on file ownership is a narrower claim that appeals to fewer people.

**What would make this the wrong pick.** It assumes buyers punish overclaiming. They may instead prefer the tool that says yes, and experience the refusals as the product being worse. That is the desirability assumption underneath the whole position, and it is entirely untested here.

## History
- 2026-08-05 unlinked "Pitch the refusals to ten prospects and count who treats them as a feature" — moved under "Buyers treat refusals as trustworthiness rather than as the product being worse" — the belief this test measures now has a node of its own

## Definition of done

"Delete each guard behind a claimed refusal in turn and require the suite to redden every time"

```
npx vitest run test/release/claimed-refusals-bound.test.ts
```

Bar: all 4 refusals the copy names are bound to a guard that reddens when the guard is disabled; 0 unbound. A refusal that survives its guard being removed is struck from the copy, not explained.

**This is the feasibility half only.** Green proves the four sentences are true and stay true. It is silent on whether a buyer reads refusals as trustworthiness or as the product being worse — that is the assumption "Buyers treat refusals as trustworthiness rather than as the product being worse", and a person is the measurement.

The command is a `no-spec` red today. The pattern it should follow already exists in this repository as the negative half — `test/release/withdrawn-claims.test.ts`, including its anti-vacuity tests in both directions — so the builder is porting a proven shape, not inventing one.
