---
type: Solution
source: 'agent-run:unattended-sweep-2026-08-27'
created: '2026-08-27'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[A grammar published in a tool description stays in step with the validator that enforces it]]

**Variation dimension: who-does-the-work. Position taken: nobody — the step is removed.**

Carry no correction at all, because no correction is issued. Each tool whose arguments are validated against a closed vocabulary states that vocabulary in its own description, in the form the validator actually accepts, so a session reading the tool list before composing already knows the rule. `ost_set_instrument` would say, in its description, that the one accepted form is `npx vitest run <path>.test.ts` with no filter, no flags and no shell punctuation — which is what `INSTRUMENT_FORMS` in `src/knowledge/instruments.ts` enforces — rather than saying "nothing else is accepted" and leaving the boundary to be discovered by hitting it.

**Why this is a different product from its siblings, not a softer version of them.** Both siblings are carriers: they accept that the refusal happens and argue about where the lesson should be stored. This one attacks the refusal's existence. If it works, the ledger has nothing to carry for this class because the class stops occurring, and the two siblings are answering a question that no longer has instances.

**What it gives up.** It only reaches rules that can be stated compactly in advance. The instrument grammar can be — it is a one-line regex over a closed list. The humans-required lane refusal cannot be, because whether a given test is labelled humans-required is a property of that node, not of the tool, and no description can tell you in advance. So this candidate covers the refusals that are about *shape* and leaves untouched the ones that are about *state*, which the observed evidence says are a real share: the 2026-08-21 session was refused twice on shape and once on state.

**Its distinctive failure mode, and it is the dangerous one.** The description and the validator become two statements of one rule that can drift apart, and the description is the half nobody tests. A description that has gone stale is worse than the current silence, because it teaches a rule confidently and wrongly, and the session believes it until refused. Any serious version of this needs the description generated from the validator rather than written beside it, which is more machinery than the sentence makes it sound.

**Where the tree already leans this way.** The same shape is already a candidate elsewhere in this vault, as "Monitor states its accepted command grammar up front rather than discovered by refusal", against the harness rather than against this product. That it has been reached for twice, independently, from two different refusal classes is mild evidence the shape is natural; it is not evidence it works, and neither instance has been tested.

Ideated by an unattended pass on 2026-08-27 against the assigned dimension. **Not blind:** this surface holds no grant to run independent parallel ideators, so all three candidates under this opportunity were composed in one context by one author — the condition the blind-ideation rule exists to prevent. Read them as one author's three answers and discount their apparent distinctness accordingly.
