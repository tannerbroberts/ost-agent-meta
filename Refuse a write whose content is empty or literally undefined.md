---
type: Solution
status: shipped
source: 'agent-ideation:2026-07-26-tenth-pass'
created: '2026-07-26'
evidence: assertion
---
#Solution #evidence/assertion
[[Empty and undefined writes actually landed in the vault histories]]

**The idea.** Put the guard at the vault instead of at the call: `Vault.annotate`, `append`, and their siblings refuse content that is empty, whitespace, or the strings `undefined`/`null`, whatever produced it.

**Contrast with its sibling.** Schema validation catches a *malformed call*. This catches a *malformed value* — including ones that arrive through a perfectly-shaped call, which is the case the schema check provably cannot see. They are complements, and this one is the last line rather than the first: it sits at the single place every write funnels through, so it holds for callers that do not exist yet.

**Why it is worth having even after v0.17.0.** The fourteen destroyed lines all share one property that is trivially detectable at the write itself and needs no knowledge of who called or why: the content was the four characters `undefined`. A guard there would have caught every one of them, including the ones from passes that used a different entry point than the CLI.

**Where it fails.** A legitimate annotation could contain the word `undefined` — this very node's history will. The rule has to be *the content is exactly that*, not *contains it*, which narrows it to almost the single observed case and makes it a tripwire rather than a policy.

⚠️ Unvalidated. Agent-ideated, from an observed failure.

## Issues
- 2026-07-27 SHIPPED, v0.18.0, 2026-07-27 (eleventh pass) — and shipped in the shape its own assumption test prescribed rather than the shape this node proposed.

"Sweep both vault histories for writes that landed as undefined or empty" was run FIRST, with its threshold fixed in advance. It found 21 undefined / 0 empty / 0 truncated across 306 annotation entries in both vaults, so the assumption held and this guard ships as a TRIPWIRE for one known shape — not as the primary fix it would have become had the sweep refuted.

Implementation: the guard sits in Vault, at the single point every node write funnels through, so it holds for entry points that do not exist yet. Covered: createNode, appendToNode, appendUnderSection, annotate, and the optional notes on setStatus, setEvidence, setLane.

The distinction this node predicted turned out to be the whole design, and it is worth recording that the prediction was right: the rule is that content IS exactly undefined/null/empty, never that it CONTAINS those words. This very node's history now contains the word repeatedly and must stay writable. A test pins that. A second test pins the subtler half — an ABSENT optional note (the JS value undefined) is a caller legitimately declining to explain itself and passes; the four-character STRING is a caller that stringified a variable it never set, and is refused. One String() apart, opposite verdicts.

21 tests, verified failing first (18 failed / 3 passed before the guard, where the 3 passing were the must-still-be-allowed cases). Full suite 482 tests / 64 files green, tsc clean. Published to npm as 0.18.0 via workflow_dispatch; registry confirms latest = 0.18.0.
- 2026-08-06 2026-08-06 In `solutionsMissingInstruments` while carrying `status: shipped` — do not write an instrument for this. A red-now command is impossible for shipped behaviour, and this pass could not verify the shipped claim: product-directory reads were denied and `ost_read_repo` was not granted, so the status rests on the node's own prose. This is the second of the two siblings that "Refuse a wiki-link that contains a newline" asked to be checked against the repository before instrumenting, and it is now the second pass in a row to defer that check for want of repo sight — the deferral is itself the finding. Unlike its sibling, no tool description on this surface describes the guard in present tense, so the shipped claim here is the weakest-supported of the five. For a human: this is the one of the five most worth confirming by hand, because if it is not shipped the status field is wrong and the queue was right. Systemic fix: "Work I already finished keeps coming back in the queue, so the pass can never say it is done".

## History
- 2026-08-05 unlinked "Sweep both vault histories for writes that landed as undefined or empty" — moved under "Empty and undefined writes actually landed in the vault histories" — the belief this test measures now has a node of its own
- 2026-08-05 status: (none) → shipped — The node's own body records this as shipped in v0.18.0 (eleventh pass, 2026-07-27), and in the shape its assumption test prescribed rather than the one this node proposed: the sweep "Sweep both vault histories for writes that landed as undefined or empty" ran first, found 21 undefined / 0 empty / 0 truncated across 306 annotation entries, so the guard shipped as a tripwire for one known shape. It sits in Vault at the single point every node write funnels through — createNode, appendToNode, appendUnderSection, annotate, and the optional notes on setStatus/setEvidence/setLane — with 21 tests verified failing first (18 failed / 3 passed, the 3 being the must-still-be-allowed cases) and the full suite green at 482 tests / 64 files. Recorded as `shipped` by the 2026-08-05 unattended sweep because it sat in `solutionsMissingInstruments` and a red-now instrument is impossible for shipped behaviour: a spec asserting the guard would pass on arrival, measure nothing, and hand a builder no definition of done. Status corrected rather than an instrument invented.
