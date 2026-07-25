---
type: AssumptionTest
status: unvalidated
evidence: assertion
source: agent-ideation — reproducible against this vault's git history
created: '2026-07-25'
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
