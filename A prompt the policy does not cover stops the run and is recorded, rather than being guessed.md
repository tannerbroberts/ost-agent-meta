---
type: Assumption
status: unvalidated
source: 'agent-ideated:2026-08-22-unattended-sweep'
created: '2026-08-22'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion

**The belief, stated so it could be false:** the shim can tell "this question matches a rule the operator wrote" apart from "this question resembles one", and on the second it stops rather than answers. The solution's whole safety case rests on that boundary: a standing yes for overwriting files that quietly generalises to a yes for deleting them is the single worst outcome any candidate under this opportunity can produce, and it is worse than the silent no the opportunity is about.

**Why it could be false.** Prompt text is prose written by third-party tools and is not a stable interface. A matcher loose enough to survive a tool rewording its question between releases is loose enough to match a different question; a matcher tight enough to be safe falls through to the stop path so often that the solution stops being a solution and becomes an elaborate way of failing. Whether a usable middle exists is the open question, and nothing about it is settled by the policy file format.

**Why this is the belief and not the operator's willingness.** The sibling ask — would an operator grant a standing yes at all — is a person's answer and is correctly theirs. But it should be asked of a mechanism that demonstrably refuses to over-match, not of a hope. An operator who says yes on the assumption that near-misses stop, in a system where they do not, has consented to something other than what was built.

**Category:** feasibility, with a potential-harm edge — this is the one assumption under this opportunity whose failure does damage rather than merely failing to help.
