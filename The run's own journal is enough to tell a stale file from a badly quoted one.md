---
type: Assumption
source: 'TRANSCRIPT:424486ec-3489-4b53-8e2b-012232d221ab'
created: '2026-08-06'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion

The classification rests on there being a recorded read to compare against. That is not free: a run may edit a file it never read this pass, may read through a tool whose output is not journalled, or may read a file that has since been rewritten by the run itself — and in each of those the hash comparison either cannot run or answers "changed" for a reason that has nothing to do with a second process.

Feasibility. The belief is that the cases where a comparison is available cover most real failed matches. If they do not, this mechanism will most often answer "cannot say", which is the one verdict that leaves the operator exactly where they started.
