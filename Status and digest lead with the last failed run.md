---
type: Solution
status: unvalidated
source: 'INBOX:2026-07-25-friction-a-pass-that-dies-on-a-driver-error-still-exits-0.md'
created: '2026-07-25'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

**The idea.** `ost-agent status` (and any digest) surfaces the most recent failed run journal first — error, when, which pass — before node counts. Failure becomes the first thing a human sees, not a JSON file to spelunk.

**Contrast with siblings:** human-visibility lane; complements rather than replaces the exit-code floor. Reuses the run journals that already exist and are already honest.

**Trade-off:** only helps if a human looks; unattended operation still needs the sibling.
