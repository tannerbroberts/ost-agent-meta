---
type: Assumption
source: 'agent-ideation:2026-09-08-unattended-sweep'
created: '2026-09-08'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion

**Risk category: feasibility** — a question about this repository's own code, answerable by a spec rather than by asking anybody.

The belief, stated so it could turn out false: *a search shape can be added to the repo channel that refuses everything the existing read already refuses — a path outside `product.repos`, the vault's own `.ost-agent/` sidecar, an unredacted secret in a returned line — without the confinement being reimplemented, and therefore without a second set of rules that can drift from the first.*

Why it could be false, and this is the real risk rather than a formality. The existing confinement is enforced on a path the caller names, before anything is read. A search does not receive a path; it produces them. So the check has to move from the argument to every result, which is a different place in the code and a different moment, and "the read is confined" does not by itself imply "a scan that discovers files is confined." A secret redactor that runs on a whole file may also behave differently when handed one matching line torn out of its context.

This is what makes the candidate cheap or expensive. If the confinement is already expressed as a reusable predicate over a resolved path, the verb inherits it and this assumption is supported. If it is inlined in the read handler, the verb needs its own copy, and a second copy of a security boundary is the thing worth knowing before anyone starts.
