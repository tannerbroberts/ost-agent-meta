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

## Issues
- 2026-07-27 SHIPPED, v0.18.0, 2026-07-27 (eleventh pass) — and shipped in the shape its own assumption test prescribed rather than the shape this node proposed.

[[Sweep both vault histories for writes that landed as undefined or empty]] was run FIRST, with its threshold fixed in advance. It found 21 undefined / 0 empty / 0 truncated across 306 annotation entries in both vaults, so the assumption held and this guard ships as a TRIPWIRE for one known shape — not as the primary fix it would have become had the sweep refuted.

Implementation: the guard sits in Vault, at the single point every node write funnels through, so it holds for entry points that do not exist yet. Covered: createNode, appendToNode, appendUnderSection, annotate, and the optional notes on setStatus, setEvidence, setLane.

The distinction this node predicted turned out to be the whole design, and it is worth recording that the prediction was right: the rule is that content IS exactly undefined/null/empty, never that it CONTAINS those words. This very node's history now contains the word repeatedly and must stay writable. A test pins that. A second test pins the subtler half — an ABSENT optional note (the JS value undefined) is a caller legitimately declining to explain itself and passes; the four-character STRING is a caller that stringified a variable it never set, and is refused. One String() apart, opposite verdicts.

21 tests, verified failing first (18 failed / 3 passed before the guard, where the 3 passing were the must-still-be-allowed cases). Full suite 482 tests / 64 files green, tsc clean. Published to npm as 0.18.0 via workflow_dispatch; registry confirms latest = 0.18.0.
