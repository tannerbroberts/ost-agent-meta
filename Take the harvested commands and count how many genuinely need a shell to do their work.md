---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: At least 70% of commands need no shell feature at all.
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that most commands do not need a shell. If a lot of real work is genuinely a pipeline, rebuilding composition and redirection above a shell-less exec means reimplementing a shell badly, with its own quoting rules people will get wrong in new ways.

**Risk category: feasibility.**

**Design.** Classify every command in the harvested transcripts: runs as a program and argument list with no shell features at all, needs one shell feature, or needs several. Weight by frequency. The share needing nothing is what a shell-less path would serve directly.

**Why it is small.** Mechanical classification over a corpus that already exists.

**What it will not cover.** It counts commands as written, and a caller who knew a shell-less path was the default would write differently. The pipelines in the corpus are also mostly ad-hoc inspection rather than load-bearing work, which this does not separate.
