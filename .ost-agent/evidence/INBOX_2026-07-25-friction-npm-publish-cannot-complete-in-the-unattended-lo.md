---
id: 'INBOX:2026-07-25-friction-npm-publish-cannot-complete-in-the-unattended-lo.md'
source: 'INBOX:2026-07-25-friction-npm-publish-cannot-complete-in-the-unattended-lo.md'
title: 2026-07-25-friction-npm-publish-cannot-complete-in-the-unattended-lo
timestamp: '2026-07-25T05:11:30.070Z'
---
# Friction (blocked): npm publish cannot complete in the unattended loop — no npm auth exists in the cloud environment, so a release commit lands but the package never ships

- **kind:** blocked
- **filed:** 2026-07-25T05:11:30.071Z
- **filed by:** bootstrap loop 2026-07-25

**Context:** v0.5.0: version bumped, changelog written, tests green, commit+tag made, but 'npm whoami' reports ENEEDAUTH and no NPM_TOKEN is present. The loop can do every part of a release except the one step that makes it real. RELEASING.md's other path (publish a GitHub Release, which fires the npm-publish workflow) is also unavailable: the git proxy rejected the tag push, so the tag the workflow keys on never reached the remote.

Filed by the agent at the moment of friction. Evidence class: **observed behavior** — self-reported by
the product's own agent, so it grounds usability, not demand, and is subject to whatever this agent
failed to notice or chose not to file.
