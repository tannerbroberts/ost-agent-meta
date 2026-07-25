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
