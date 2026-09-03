---
type: Assumption
source: 'TRANSCRIPT:9c00df65-1c8d-4171-a870-22efc103d834'
created: '2026-09-03'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion

**Risk category: feasibility.** Stated so it could be false: a pre-flight parser has to recognise constructs the engine it is protecting does not implement, which means it cannot simply hand the pattern to that engine and watch it fail — it must independently parse a dialect wider than the one it runs on. If the parser's own grammar is narrower than the caller's pattern in some corner, it will either miss a construct (the caller still fails at run time, and now twice) or claim one that is actually supported (a false refusal, which is strictly worse than the status quo).

The false-refusal direction is the one that kills the candidate. A caller who is told a valid pattern is invalid has no recourse and no way to check, and one such incident costs more trust than the N-calls-to-one-call saving buys.

**What would settle it:** a spec that submits patterns carrying several unsupported constructs and asserts every one is located, plus patterns that are entirely supported and asserts none is flagged.
