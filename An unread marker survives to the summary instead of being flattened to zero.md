---
type: Assumption
status: unvalidated
source: 'TRANSCRIPT:5e5c119d-e5e8-4dbd-ab7c-c4bfc1247a18'
created: '2026-08-06'
evidence: observed
---
#Assumption #unvalidated #evidence/observed
[[Feed every search path a malformed pattern and require the total to say two were unread]]

**Feasibility.** Introducing a third return state is easy. Getting it to survive the journey to the number an operator reads is the claim.

Stated so it can be false: every consumer between the search and the summary preserves the distinction between "examined and found nothing" and "could not examine". The pressure runs the other way at each boundary. A caller that wants a count writes `results.length`. A caller that wants to filter writes `results.filter(...)`. Both flatten unread to zero, both are the obvious thing to write, and neither looks wrong at the call site — the harm only appears three layers up, in a total that reads as complete.

This is the same failure the tree already records at the sweep layer: a sweep that cannot read its subject reports a clean result. The unread marker is the fix for it, and the fix has the same shape as the disease, because a marker that is dropped is worse than no marker — it produces the same wrong number with a mechanism in place that everyone believes is protecting them.

Where it could be true: if the search interface never returns a plain collection, and the only way to reach a count is through a call that forces the unread case to be handled, then the flattening path is absent rather than discouraged. That is a stronger property than a convention and it is the version worth building.

Where it stays false no matter what: anywhere a pass reports in prose. This pass wrote several summaries by hand, and a model composing a sentence about what it found has no type system stopping it from saying "no issues" over a subject it could not read. That limit should be stated rather than designed around.
