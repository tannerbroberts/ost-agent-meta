---
type: Assumption
status: unvalidated
source: 'TRANSCRIPT:8a9777ad-a1ca-47fc-ab8e-3bd4b001a5cd'
created: '2026-08-06'
evidence: observed
---
#Assumption #unvalidated #evidence/observed

**Feasibility.** The whole preflight rests on this and nothing else: that the set of tools a session is permitted to invoke is readable before the first invocation.

Stated so it can be false — it may well be false. Nothing in the record shows a run ever discovering its grant except by being denied. Every one of the fifteen denials across five sessions arrived as a tool error in response to a call that had already been composed. If permission is only ever evaluated at call time, and the answer is only ever delivered as a refusal, then there is no cheaper channel and a preflight can do nothing but make the same fifteen calls earlier and in a batch — which is not a preflight, it is the same night with the disappointments reordered.

Two ways it could be true. The permission configuration is a file on disk and the run can read it and compare names, which needs no new protocol at all. Or the harness exposes the resolved tool list to the session, in which case the comparison is a set difference against the skill's declared `allowed-tools`.

Two ways it could be false. The grant may be evaluated per call against rules that are not enumerable in advance — a pattern match on arguments, a per-path decision like the `Glob` denials on `/Users/tanner/dev/OST-Agent`, which were about the path and not the tool. Those cannot be answered by any list, and a preflight that reports "Glob: granted" would be lying about exactly the case that failed five times.

That last point matters more than the rest, because four of the fifteen recorded denials were path-scoped rather than tool-scoped. If the preflight can only reason about tool names, it clears a run that is about to be blocked anyway.
