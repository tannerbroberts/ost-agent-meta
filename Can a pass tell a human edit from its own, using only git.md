---
type: AssumptionTest
status: unvalidated
source: agent-ideation — reproducible against this vault's git history
created: '2026-07-25'
evidence: assertion
instrument: npx vitest run test/git/hand-edit-detector.test.ts
authorship: machine
---
#AssumptionTest #ported-from-ost-agent-vault #evidence/assertion

**Assumption under test (feasibility).** That human edits are cleanly separable from tool-driven ones using only what git already records — no new state, no file watching, no daemon.

**Why it looks true, and why that is not the same as being true.** Every tool-driven change lands as a commit whose subject matches `mcp: <tool_name> — …`. The hand-edit of 2026-07-24 landed as an *uncommitted* working-tree change: one file emptied, one file untracked. Those two populations look trivially distinguishable. The test is whether that holds up outside the one case that inspired it.

**Proposed test — adversarial, against the real history.** Run the detector over this vault's full history and the tetrix vault's, and check it finds exactly the known human edits and nothing else. Then try to break it deliberately: a human edit committed by hand with a plausible `mcp:`-style subject; a human edit made while a pass is mid-write; an edit that only changes frontmatter; an Obsidian rename that *does* rewrite inbound links, leaving no empty file behind; a `git stash`, a branch switch, an amended commit. Also run it against a vault with no human edits at all and confirm it stays silent.

**Pre-commit the threshold.** Zero false positives on clean history — a drift report that cries wolf is worse than none, because the operator learns to skip it and then misses the real one. False negatives are acceptable if they fail toward silence rather than toward a confident wrong story about what the human meant. And the detector must report *what changed* in terms of nodes and links, not just which files are dirty: "the Outcome's link target is now empty and a new node carries its 8 links" is actionable; "2 files changed" is not.

**What a failure here would actually tell us.** If git alone cannot separate the populations reliably, the fallback is worse than it sounds — the pass would need its own record of what it wrote, which is duplicate state that can itself drift, and the append-only trust story gets harder to explain. So a negative result here is not a small setback; it substantially raises the cost of the whole sibling opportunity. Worth knowing before anything is built on top of it.

⚠️ Proposed only — the agent does not run tests.

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-04 instrument: (none) → npx vitest run test/git/hand-edit-detector.test.ts — The threshold — zero false positives on clean history, failing toward silence, and reporting what changed in nodes and links rather than files — is settled by git fixtures the spec builds itself: the adversarial cases the node lists (a hand edit committed with an `mcp:`-style subject, a frontmatter-only edit, a rename that rewrites inbound links, a stash, a branch switch, an amended commit) plus a clean-history control. It fails today because no detector exists.
- 2026-08-04 instrument: npx vitest run test/git/hand-edit-detector.test.ts → npx vitest run test/git/human-vs-agent-edit-attribution.test.ts — The question is literally whether git alone carries enough signal, so the answer is a classifier over a fixture repository seeded with both kinds of edit — agent commits made through the tool surface and hand edits made outside it — scored against the known truth; it fails today because no attribution pass exists.
- 2026-08-04 instrument: npx vitest run test/git/human-vs-agent-edit-attribution.test.ts → npx vitest run test/git/hand-edit-detector.test.ts — Restoring the instrument this test already carried; the preceding replacement in this History was made in error, from misreading the default `needsHumans` lane as an instrument gap.
- 2026-08-06 instrument: npx vitest run test/git/hand-edit-detector.test.ts → npx vitest run test/git/authorship-attribution.test.ts — Fails today because no attribution module exists: nothing in the vault's git layer distinguishes a commit an agent pass authored from one a human made by hand, so the spec has nothing to assert against. Written blind of the repository — this sweep holds no repo-read grant, so the spec path names behaviour that does not exist rather than assertions that go red against today's code.
- 2026-08-06 instrument: npx vitest run test/git/authorship-attribution.test.ts → npx vitest run test/git/hand-edit-detector.test.ts — Restoring the instrument this test already carried. The 2026-08-06 unattended sweep replaced it in error, having read `assumptionWork.needsHumans` as meaning "no instrument" when it means "no result yet and no compute-only lane label". No permit was in force to lose, and the original path is the one a builder should work to.

## Instrument Log
- 2026-08-04 **red** (exit 1) `npx vitest run test/git/hand-edit-detector.test.ts` — No test files found, exiting with code 1
- 2026-08-31 **green** (exit 0) `npx vitest run test/git/hand-edit-detector.test.ts` — ✓ a hand edit committed with an `mcp:`-style subject > THE BOUNDARY: a careful forgery is invisible, and fails toward silence rather than a wrong story 907ms
