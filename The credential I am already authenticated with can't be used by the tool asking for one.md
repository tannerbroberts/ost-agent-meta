---
type: Opportunity
status: unvalidated
source: 'INBOX:2026-07-25-friction-run-p2-p5-requires-an-api-credential-even-when-a.md'
created: '2026-08-02'
evidence: stated
---
#Opportunity #unvalidated #evidence/stated

The blocking case is narrower than not wanting to buy a key: an authenticated agent session was driving the run, with a live model connection right there, and the path still refused to start because it looked for a separate API credential and found none — no environment variable, no CLI, an empty keychain entry.

The work was possible the whole time; it was reachable only by routing around the intended path through the ambient tool surface. So the cost is not the price of a key, it is that the obvious way in is closed to the person who already has everything they need, and the way that works is not the documented one.

**The need:** I want the run to use the authentication I am already holding, instead of asking me to acquire a second one to do what this session can already do.

More than one way to address this: inherit the host session's authentication, delegate model calls back to the driving agent, detect the ambient path and prefer it automatically, or fail with a message that names the ambient route rather than the missing variable.

## Provenance

Distilled from `INBOX:2026-07-25-friction-run-p2-p5-requires-an-api-credential-even-when-a.md` — filed by the twenty-passes ambient driver after the SDK could not resolve an authentication method while an authenticated session was active.
