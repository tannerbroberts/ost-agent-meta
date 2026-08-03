---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Try to express every refusal this tool can issue as a precondition, and count the ones that resist]]

Every refusal a tool can issue is expressible as a condition over things knowable in advance — this parent exists, this layer may sit under that one, this source has earned at most this rung, this heading is reserved. Publish those conditions as data the caller can read and evaluate before composing a call, rather than discovering them one refusal at a time.

The usage trace shows exactly this shape: three failed calls in a day, all the same refusal, all about an evidence ceiling that was fully determined by the source before the call was written. Nothing about those failures needed a round trip.

**Compared to the alternatives.** Removes whole classes of failure rather than making them cheaper, and it costs nothing at run time once published. It requires the conditions to be genuinely expressible outside the tool, and any that are not will still be discovered the hard way — so the improvement is real but partial. Richer error messages help after the fact; a dry-run mode still spends the round trip.

**What would make this the wrong pick.** Published preconditions are a second copy of the rules, and a second copy drifts. A caller checking against a stale description will be confidently wrong, which is worse than being told no.
