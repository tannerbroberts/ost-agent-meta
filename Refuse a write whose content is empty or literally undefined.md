---
type: Solution
source: 'agent-ideation:2026-07-26-tenth-pass'
created: '2026-07-26'
evidence: assertion
---
#Solution #evidence/assertion
[[Sweep both vault histories for writes that landed as undefined or empty]]

**The idea.** Put the guard at the vault instead of at the call: `Vault.annotate`, `append`, and their siblings refuse content that is empty, whitespace, or the strings `undefined`/`null`, whatever produced it.

**Contrast with its sibling.** Schema validation catches a *malformed call*. This catches a *malformed value* — including ones that arrive through a perfectly-shaped call, which is the case the schema check provably cannot see. They are complements, and this one is the last line rather than the first: it sits at the single place every write funnels through, so it holds for callers that do not exist yet.

**Why it is worth having even after v0.17.0.** The fourteen destroyed lines all share one property that is trivially detectable at the write itself and needs no knowledge of who called or why: the content was the four characters `undefined`. A guard there would have caught every one of them, including the ones from passes that used a different entry point than the CLI.

**Where it fails.** A legitimate annotation could contain the word `undefined` — this very node's history will. The rule has to be *the content is exactly that*, not *contains it*, which narrows it to almost the single observed case and makes it a tripwire rather than a policy.

⚠️ Unvalidated. Agent-ideated, from an observed failure.
