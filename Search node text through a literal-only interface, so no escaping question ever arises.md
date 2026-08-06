---
type: Solution
status: unvalidated
source: 'TRANSCRIPT:8a9777ad-a1ca-47fc-ab8e-3bd4b001a5cd'
created: '2026-08-06'
evidence: observed
---
#Solution #unvalidated #evidence/observed
[[Nearly every search a pass issues is a literal lookup wearing a pattern language]]

Remove the pattern language from the path where node text is searched, rather than learning to quote for it.

Every recorded failure of this kind has the same origin: a sentence a person wrote — a node title containing a brace, an asterisk, a quote — was handed to something that reads punctuation as instruction. `{Charge` and `*{threshold` were never patterns. They were the first characters of two titles in this vault.

The proposal is a search entry point that takes text as data and nothing else. No glob, no regex, no shell word-splitting: a caller asks "which nodes contain this exact string" and the question cannot be malformed, because there is no syntax to malform. Where a pass genuinely needs pattern matching it reaches for a different, explicitly-named call, and that call's arguments are written by hand rather than interpolated from tree content.

The bet is that the overwhelming majority of searches a pass actually issues are literal lookups wearing a pattern language's clothes. If that is true, this candidate eliminates the entire class rather than mitigating it, and it does so at the boundary rather than at every call site — which is the difference between a fix and a discipline.

If it is false — if passes routinely need real pattern semantics over node text — then a literal-only interface just moves the calls to the escape hatch and the failures come back through it. That is the assumption worth settling before building, and it is settled by counting, not by arguing: the searches a pass issues are recorded.

Against its siblings. "Never let a malformed search be counted as an empty result" is strictly more robust and strictly less satisfying — it tolerates the failure and prevents the miscount, and it keeps working for denied reads and size caps that no escaping fixes. "Route every data-derived argument through a quoter" keeps the pattern language and adds a rule that must be remembered, which is the shape of fix this project has elsewhere concluded is not enough on its own. This candidate is the only one of the three that makes the mistake unavailable rather than survivable, and it is also the only one whose scope claim might be wrong.

## Definition of done

"Census the recorded searches and split them by whether their argument came from the tree"

```
npx vitest run test/telemetry/search-literality-census.test.ts
```

Red today: the trace records search invocations but nothing classifies them by pattern-need or by argument provenance, so the census has nothing to read.

Run this before building. It is as likely to redraw the solution as to confirm it — if tree-derived arguments turn out to be overwhelmingly literal while hand-written ones are freely patterned, the interface should be drawn on provenance, not on literalness, and this node wants rewriting rather than implementing.

Green here bounds only searches over node text. The shell failures in the same opportunity — a path globbed, a flag read as a filename — are untouched by it.
