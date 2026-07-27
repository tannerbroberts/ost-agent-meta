---
type: Solution
created: '2026-07-27'
evidence: assertion
---
#Solution #evidence/assertion

**The idea.** Any tool that reports "N found" also reports "over M examined, K unreadable". The operator reads a ratio, never a bare integer.

**Why this one first.** It is the smallest change that makes the failure *visible without being anticipated*. The em-dash bug was not on anyone's list; a denominator would have shown 302 of 306 entries examined and 4 files unreadable without anyone having thought about filename quoting in advance. Guards catch the failures you predicted. A denominator catches the ones you did not.

**Where it fails.** A denominator computed by the same broken traversal is just as wrong — if the walker never enumerates the em-dashed file at all, M excludes it and the ratio reads 100%. This only works when the denominator comes from a DIFFERENT source than the counter (directory listing vs. git, say), which is more than a print statement and is the real cost of the idea.

⚠️ Unvalidated. Agent-ideated from an observed failure.
