---
type: Opportunity
source: 'TRANSCRIPT:4ff7b605-da1d-4f2e-8c05-ec6408118837'
created: '2026-08-05'
evidence: observed
---
#Opportunity #unvalidated #evidence/observed
[[The surface publishes its accepted grammar where a composer can read it before writing]]
[[Validate incrementally as the artifact is built, so the rejection arrives at line three]]

I write a long artifact for a surface I cannot inspect first, hand the whole thing over, and the rejection arrives at a line number.

Twice on record: `4ff7b605` rejects a workflow script at `(172:33)`, and `516fdfb8` rejects one at `(24:12)`. Both refusals name the same cause — the script must be plain JavaScript, and the usual reason it is not is TypeScript syntax: type annotations, interfaces, generics. So a hundred and seventy lines were composed in a dialect the surface never accepted, and nothing said so until the whole thing was submitted.

The refusal is well-written; it explains the cause and lists the common ones. That is not what is missing. What is missing is that **the constraint is only discoverable by violating it.** The dialect a target surface accepts is a property of the resource, and the resource does not hand it over — so I guess, and the exit code is the answer. That is the parent need in a specific and expensive form: guessing is cheap when the artifact is one line and costly when it is a hundred and seventy.

It is worth separating from the case where a symbol is wrong and a typecheck at the end of the batch catches it. That one is about *when* a check runs over code in a repository I can read. This one is about a foreign surface whose grammar I have no way to read at all, so there is nothing to check against locally, however early I check.

More than one way to address it: the surface publishing its accepted grammar where a composer can read it before writing; validating incrementally as the artifact is built rather than at submission; a cheap dry-run that parses without executing; or the composer being handed a skeleton in the accepted dialect so the default shape is already legal.

Evidence class is observed behaviour — the agent's own tool use, captured mechanically from session transcripts. It grounds usability, not desirability.
