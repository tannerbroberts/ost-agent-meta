---
type: Solution
source: 'TRANSCRIPT:0459d729-8ee3-43fc-ae1f-f05928ad84e2'
created: '2026-08-18'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[The harness can reliably tell created by this session apart from pre-existing, this session just wrote to it]]

Narrow the guard's scope: a file the session created with its own Write call this run cannot hold content the session hasn't seen (it wrote all of it), so a subsequent Edit to that same file should not require an interposed Read. Only files that existed before this session touched them, or that another process could have changed, need the guard.

**Compared to the alternatives.** Removes a real subset of the false-positive friction (editing a file you just created) without changing the guard's behavior anywhere it is actually protective, and needs no new mechanism beyond tracking session-created paths. Narrower fix than the other two: it does nothing for the case of editing a pre-existing file the session genuinely never read.
