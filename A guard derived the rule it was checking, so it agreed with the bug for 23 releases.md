---
type: Opportunity
status: unvalidated
source: 'TRANSCRIPT:89ac8277-29ce-4d80-827e-cefea0bebabf'
created: '2026-08-06'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion

**The observation (2026-08-06).** Every tool grant this product ships to a plugin session — eight command files and the generated skill — named tools that no plugin session mints. Claude Code namespaces a directly-registered server `mcp__<server>__` and a plugin-delivered one `mcp__plugin_<plugin>_<server>__`; both names here are `ost-agent`, so the short form read as correct. Confirmed by probing a live session, not by reading docs.

Interactively the mismatch is one permission prompt per tool. Under `claude -p` there is nobody to prompt, so **an ungranted call is denied rather than asked about**: the pass runs, every call is refused, it writes nothing, and it exits 0 reporting success. `docs/consuming-from-claude-code.md` records five scheduled firings already spent on exactly that, and had documented the mismatch as "harmless, just a prompt".

**Why this is not the same node as "a failed pass reports success".** That one is about a pass that *died* and reported clean. This is a pass that ran perfectly, made every call it meant to make, was refused every time, and reported clean — with a health record showing both phases green. The failure was upstream of anything the loop can observe about itself, in a *grant string* that no runtime check reads.

**The part worth a node of its own: the guards agreed with the bug.** Three files derived the prefix independently — the skill generator and two release tests — and all three derived it the same wrong way. Each carried a comment explaining that *deriving* it from the manifest, rather than hardcoding it, was what made it trustworthy. So the repo had three guards, each documented as protecting this exact property, and the property was false the whole time. Three independent derivations of one rule are three copies of whatever the first author believed. Deriving is not the same as deriving correctly.

**The general shape, which is what makes this an opportunity rather than a bug report.** A check that *computes* the thing it is checking cannot fail when the computation is wrong — it can only fail when the two sides disagree, and they never disagree if they share an assumption. Every guard in this repo that derives its expectation from the same source as the thing under test has this property. What distinguishes a guard that would have caught it: an *observation* in the check — a literal recorded from a real run, which is what the fix now carries, with the probe command written above it so the next person can re-take it rather than trust it.

**What this costs, if it generalises.** This tree's entire believability argument rests on gates that are trusted because they are mechanical. A mechanical gate that shares its premise with its subject is a gate that reports what it assumed. Nobody has counted how many of this repo's checks have that shape — the honest answer today is that one of them was found by accident, while chasing something else.

## Provenance

Found while resolving four untracked files that were reddening the local suite. The file that named the defect had been written in an earlier session and never committed, which is its own instance of the parent problem: the finding existed, on disk, unread, for days.

## Issues
- 2026-08-06 unresolved-citation (flagged by ost_check, repaired by nobody yet): frontmatter cites `TRANSCRIPT:89ac8277-29ce-4d80-827e-cefea0bebabf`, and no record under `.ost-agent/evidence/` carries that id. Three sibling nodes created in the same sitting — "A perf gate reports its measurement next to the number the criterion recorded", "Every self-observation channel names which of its sources each item came from", and "Three gates fired correctly in one session and every one of them read as noise first" — cite the exact same missing id, so this is one fault repeated four times, not four faults. Most likely cause: the pass cited the id of the session it was running in, which the transcript adapter cannot have stored yet because that session had not ended. What would settle it: check whether `89ac8277-29ce-4d80-827e-cefea0bebabf` appears as a Claude session file on this machine; if it does, re-ingesting will resolve all four at once and nothing else is wrong. If it does not, the id was invented and the four nodes rest on nothing — their evidence rung should come down to `assertion`. No tool on this surface can rewrite a node's `source` frontmatter, so the repair is a human's; this pass could only record the diagnosis.
