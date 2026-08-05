---
type: Solution
created: '2026-08-05'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Check a derived deny rule against legitimate uses of the same verb it was derived from]]

**The mechanism: stop remembering, start narrowing.** The first time a guard refuses a class of call, it writes the refusal into the workspace's own configuration as a standing deny rule. The correction is not something a later session has to recall — it is a property of the environment that session runs in. The eighth `sleep`-then-poll is not resisted by a better-informed composer; it is simply not a thing that can be done here.

**Why this shape.** It removes the reader from the loop entirely, which is the one weakness the ledger sibling cannot design around. The observed failure is a reflex surviving seven explicit, well-written corrections — so a mechanism whose success depends on the reflex being talked out of itself is betting against the only data there is. This one does not need the agent to learn anything.

**Compared to its siblings.** Strictly the most reliable of the three at preventing the specific repeat, and the only one whose effect does not decay with how much the composer is paying attention. It is also the most dangerous, and the asymmetry is the point: a ledger entry that is wrong costs a confused reader, while a deny rule that is wrong costs every future session a capability, silently, with the refusal looking exactly like the correct guard it was derived from. Narrowing an agent's own capability to satisfy a gate is already a named worry in this tree — [[The agent narrows its own capability to get past a gate I set]] — and this candidate is a machine for doing precisely that.

**What would make this the wrong pick.** If the class the guard inferred is wider than the class that was wrong. `sleep` before a poll is refused; `sleep` in a fixture that needs a real delay is not, and a rule derived from the first will eat the second. Anything shipped here needs the constraint to be reviewable and reversible by a human, and probably needs the human to author the generalisation rather than the guard.

⚠️ Unvalidated. Agent-ideated on 2026-08-05. Note that this is the agent proposing to have its own future capability narrowed automatically, which is a proposal it is not a neutral party on in either direction.

## Definition of done

[[Check a derived deny rule against legitimate uses of the same verb it was derived from]]

`npx vitest run test/security/derived-deny-rule.test.ts`

Zero false refusals across a corpus of legitimate uses, and every derived rule attributed to its source refusal and reversible by one human action. Red today because no rule is derived from a refusal at all. It cannot find the capability nobody realised was lost — that one is absent from the corpus by definition.
