---
type: Solution
source: 'TRANSCRIPT:1744f10a-e7ce-4e46-a573-a1d99c44960c'
created: '2026-08-06'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A generated manifest can only carry the rules the schemas know, and the refusal that bit hardest is not one of them]]

**The idea.** The run reads one machine-generated manifest at startup that states, per tool, the preconditions a caller cannot otherwise see: that a write requires a prior read of the same path, that a response is refused above a size, that a parameter set is closed, that an evidence rung is capped by provenance. The cost of each rule is paid once, at composition time, instead of a turn at a time in the middle of unattended work.

**Why this shape.** The parent opportunity's census establishes that the refusal text is already correct and already names the remedy — the run complies the same turn, every time. So the constraint is not clarity, it is arrival time. A manifest changes when the rule reaches the caller, and changes nothing about what the rule says.

**How it differs from its siblings.** This one teaches. "The surface satisfies a precondition it could have satisfied itself" removes the rule instead of teaching it, and "Every response that can be refused for size states its size first" makes one class of limit observable rather than declaring all of them. This is the broadest and the cheapest to author, and it is also the weakest: a manifest is only as good as the caller's willingness to read it before acting.

**Where this fails, stated so it can be judged.** A run that receives a manifest may still compose the colliding call — the corrections header this vault's own unattended runs already carry is a partial instance of this idea, and sessions still hit refusals it did not cover. A manifest also has to be generated from the surface rather than written by hand, or it becomes a second statement of the rules that drifts from the first, which is the failure recorded under "A guard derived the rule it was checking, so it agreed with the bug for 23 releases".

**Cost.** Generation from the existing tool schemas plus a startup read. No new refusal, no new state.

⚠️ Unvalidated. Agent-originated, from the agent's own transcripts — usability evidence, not evidence that anyone wants this.

## Definition of done

"Measure what fraction of recorded refusals a schema-derived manifest could have named"

```
npx vitest run test/preflight/manifest-covers-observed-refusals.test.ts
```

Green means a manifest generated from the tool schemas alone names a rule covering at least 60% of the distinct refusal classes in the captured transcript corpus. Below that bar the solution's cost argument is refuted rather than refined, because the rules that actually bite would be living outside the schemas it generates from.

Named in plain text rather than linked: the test's one wikilink is held by its parent assumption, "A generated manifest can only carry the rules the schemas know, and the refusal that bit hardest is not one of them".
