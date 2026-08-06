---
type: Solution
source: 'agent-ideation:2026-08-06-unattended-sweep'
created: '2026-08-06'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

**The idea.** Any check whose subject is a contract with something outside the repository — a namespace another runtime mints, a registry's published version, a shell's globbing behaviour — may not compute its expected value. It asserts against a literal captured from a real run, and the probe command that produced that literal is stored on the line above it, so the next reader can re-take the observation instead of trusting it.

**Why this shape.** It is the fix that actually worked, promoted from an instance to a policy. The parent opportunity records that three guards each derived the plugin prefix from the manifest, each carried a comment explaining that deriving rather than hardcoding was what made it trustworthy, and all three were wrong together for 23 releases. The repair that ended it was a literal taken by probing a live session. The generalisation is that a derived expectation inherits its author's belief, whereas a recorded one inherits reality — and the stored probe command is what keeps the recording from silently going stale, because it converts "trust this constant" into "here is how to check this constant."

**How it differs from its siblings.** This one changes what a guard is *allowed to assert against*, and only for external contracts. "Require every guard to demonstrate it can fail" leaves the assertion alone and tests the guard instead. "A census of every check whose expected and actual share a provenance" neither changes nor tests anything — it finds the population, and is the cheapest of the three because it is read-only.

**Where it fails, stated so it can be judged.** A recorded literal rots. The observation was true of one runtime version on one machine on one day, and nothing makes the world re-take it; a stored probe command that nobody runs is a comment. It also needs a boundary — which contracts count as external — and that boundary is itself a judgement someone will get wrong. Applied too widely it turns every check into a golden-file test, which is the failure mode where the expected value is updated to match whatever the code now does.

**Cost.** A policy plus a lint that recognises the pattern. No new runtime machinery.

⚠️ Unvalidated. Agent-ideated from the agent's own repository, generalising one repair into a rule — which is exactly the move the parent opportunity warns produces confident wrong guards, and a human should weigh that irony rather than let this pass unremarked.
