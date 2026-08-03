---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

The run appends one line per completed step at the moment it completes — what was attempted, what it produced, and that it finished. A run that is killed, times out, or dies leaves a journal whose last line is the last thing that actually worked. Reading the state of a half-finished run becomes reading the end of a file, rather than inferring from side effects.

The crucial property is that the journal is written forward. Anything summarised at the end is the thing that is missing precisely when it is needed.

**Compared to the alternatives.** Answers the question directly and cheaply, and needs nothing beyond an append per step. Against recording the directory and argv of each step, it says what was done rather than where — the two are complementary and probably belong in the same line. What it does not do is make the run resumable; knowing where it stopped is not the same as being able to continue from there, and a reader may want the second thing having been given the first.

**What would make this the wrong pick.** A step that half-finished is the interesting case and the one this handles worst: it either logs before completion and overstates, or after and understates. Which of those failure modes is acceptable is a decision that has to be made deliberately rather than discovered later.
