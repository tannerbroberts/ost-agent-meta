---
type: Assumption
source: 'agent-run:unattended-sweep-2026-08-27'
created: '2026-08-27'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion
[[A description that disagrees with the grammar its own validator enforces fails the suite]]

**Risk category: feasibility.**

The belief, stated so it could turn out false: a tool description that states the accepted grammar can be kept true as the validator changes, rather than drifting into a confident lie.

**How it could be false.** The description and the validator are two statements of one rule living in different files, and only one of them is executed. `INSTRUMENT_FORMS` in `src/knowledge/instruments.ts` is exercised by every call; the sentence in the tool description is exercised by nobody. Someone widens the grammar to admit a second form, updates the regex, ships — and the description now understates what is allowed. Someone narrows it and the description now overstates. Nothing goes red either way.

**Why this is the sharpest risk for this candidate.** A stale description is strictly worse than the status quo this node is trying to improve on. Today a session composes wrong, gets refused, and is told the truth in the refusal. With a stale description it composes wrong having been told a falsehood *and* is refused — so the pass pays the same call plus the cost of having been misled, and the correction it does eventually get contradicts documentation it was handed as authoritative.

**What would make the belief hold.** The description generated from the validator rather than written beside it, or a check that fails when the two disagree. Both are more machinery than "just document it" implies, and whether that machinery is worth building is the real question under this candidate.

**What settling it does not settle.** Whether a published grammar actually prevents the refusal — a session has to read and use the description, which is a usability belief about the reader, not a feasibility one about the text. That needs its own test.
