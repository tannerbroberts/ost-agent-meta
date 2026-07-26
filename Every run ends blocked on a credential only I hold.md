---
type: Opportunity
status: unvalidated
source: 'INBOX:2026-07-25-friction-npm-publish-cannot-complete-in-the-unattended-lo.md'
created: '2026-07-25'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion

The unattended loop can do every part of a release except the one step that makes it real: publishing requires an auth secret that exists only on my machine. A run that ends 99% complete still lands on my desk.

Grounding: on 2026-07-25 the cloud bootstrap loop prepared v0.5.0 fully — version bump, changelog, green tests, commit and tag — then stalled: npm whoami returned ENEEDAUTH, no NPM_TOKEN in the environment, and the git proxy rejected the tag push that would have fired the release workflow (agent-filed friction, kind: blocked).

Litmus: a scoped token in the runner environment; OIDC trusted publishing; keying the release workflow off something the loop can push; a queued human-confirm publish step — multiple distinct ways. Distilled by the mapping agent from agent-self-reported observation; unvalidated.

## Issues
- 2026-07-26 undefined
- 2026-07-26 **Disconfirmed as framed — three releases now published from inside the loop, no credential (rung: observed; our own system, run rather than merely read).** v0.14.0 and v0.15.0 shipped on the ninth pass; **v0.16.0 and v0.17.0 shipped on this one**. `npm whoami` in this container is still ENEEDAUTH and must be. Nothing about the credential situation changed. — The chain was never *auth*, it was *trigger*: the publish workflow's only trigger was a manually-published GitHub Release, the documented route to that runs through a pushed tag, and this environment's git proxy answers `git push --tags` with HTTP 403 (re-confirmed this pass when the v0.16.0 tag was refused). Each link needed a person; none of them was the secret everyone was staring at. NPM_TOKEN sat in the repo's Actions secrets the whole time — exactly where it belongs and exactly where this container cannot reach it. The safety property was never the obstacle. The fix was `workflow_dispatch`, a trigger the workflow had carried since the day it was written. — **What this does NOT retire:** the general need (an unattended run stalling on the one step only a human can take) is real and this node should stay. What is retired is this instance, and the habit that produced it — a blocker asserted once from a true observation (ENEEDAUTH), carried forward verbatim through eight briefings, never re-derived, growing more confident each restatement and less examined. **Left as an annotation, not a rewrite:** whether this node should be re-framed around unpushable release triggers, or closed and replaced, is a human's call, and the party that spent eight passes mis-framing it is not the neutral one to make it.
- 2026-07-26 **Hygiene — a destroyed annotation, flagged not repaired (2026-07-26).** One or more lines in this node read `- <date> undefined`. That is not a note anybody wrote: `ost_annotate` was called with `note` instead of its declared `issue` field, nothing validated the call, and the literal string "undefined" was appended in place of the content. The original text was never written anywhere and is unrecoverable. Fourteen such lines exist across the two live vaults, written by several passes over three days. The cause is closed in ost-agent v0.17.0, which refuses a tool call that does not match the schema the tool itself declares. **Left in place deliberately:** this vault is append-only, and rewriting history to hide a bad write is exactly the action this product refuses — including when the product is the one that made it. Full account: [[A tool call I got slightly wrong destroyed the note I was filing]].
