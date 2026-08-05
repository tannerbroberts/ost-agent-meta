---
type: Solution
source: 'agent-ideated:2026-08-02-maintenance-pass-2'
created: '2026-08-02'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Reverted commits and discarded branches carry the dead ends a transcript would have shown]]

**The idea.** Never read a transcript at all. Read what the work left behind: commits that were reverted, branches built and discarded, files created and deleted inside one pass, tests written then removed, a plan file rewritten mid-pass, work pushed that duplicates work already on the trunk. A wrong framing that cost real time almost always leaves a scar in the artifact record even when it leaves no error code — because someone had to undo it.

**Why this is not "Mine tool errors and retries from run logs".** That sibling mines the *log* for failures the machine already flagged, which is the same population the harvester scans and the same population the parent's census has now measured as useless for this purpose. This mines the *repository* for reversals the machine never flagged at all. Nothing in a revert is an error: every command in a wrong-turn pass can exit 0, every test can pass, and the whole thing can still be deleted the next morning.

**Its strongest evidence is already in this vault, which is the argument for it.** The 2026-07-26 collision recorded on "Two agents sharing my vault can trample each other" cost roughly eight hours of building and was discovered by a rejected `git push` after every cost had been paid. Nothing errored. A transcript reader would have seen a competent, confident session. The artifact record, by contrast, holds the whole story plainly: a commit, a rejected push, a deletion, and one salvaged test file. That failure is *invisible* to both sibling candidates and legible to this one.

**Where it is blind, and this is the sharp trade.** It can only see friction that touched a file. A pass that spent four hours reasoning down a wrong path and then wrote the right code leaves nothing to find; so does a wrong framing inside the OST itself, which is append-only and by design never reverts anything. It is also the only candidate here that produces no evidence for a discovery pass over a vault with no code repository at all — and per "The agent has to guess what resources it's actually working with", the product cannot assume there is one. Against that: it needs no model, no extra tokens, no credential, and no cooperation from the agent being observed, which makes it the only candidate that keeps working when the operator's compute budget is the binding constraint.

⚠️ Unvalidated. Agent-ideated during the 2026-08-02 maintenance pass. The three candidates under this opportunity are deliberately different mechanisms with different blind spots; they should be compared, not ranked on plausibility.

## Definition of done

"Replay two hundred commits and count what a dead-end scan flags"

```
npx vitest run test/git/dead-end-scan.test.ts
```

Green means the scan finds abandoned trails in the committed record without needing the session that produced them — the premise of reading dead ends off artifacts. It does not settle whether the dead ends worth knowing about *reach* the artifact trail at all: an approach abandoned before anything was committed leaves nothing here to find, and that is precisely the cheapest kind to abandon.

## History
- 2026-08-05 unlinked "Replay two hundred commits and count what a dead-end scan flags" — moved under "Reverted commits and discarded branches carry the dead ends a transcript would have shown" — the belief this test measures now has a node of its own
