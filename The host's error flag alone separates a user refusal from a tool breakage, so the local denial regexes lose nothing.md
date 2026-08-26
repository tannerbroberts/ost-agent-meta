---
type: Assumption
created: '2026-08-26'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion

**The belief, stated so it could be false:** a transcript record carries enough host-written structure to tell "a person declined this" from "this call broke" without matching `DENIAL_PATTERNS` against the result text — so deleting those regexes costs no distinction the channel currently makes.

**Risk category: feasibility.** It is a question about what fields the stored records contain, and the repository plus the captured corpus can answer it.

**How it could turn out false, and the code already hints that it is.** `DENIAL_PATTERNS` exists at all, and it is three regexes matching English prose (`user doesn't want to proceed`, `permission was denied by the user`, `user rejected`). Regexes over prose are what someone writes when the structured signal is not there. If `is_error: true` is the only marker both cases share, then the flag has already merged them and this candidate's whole premise — that the host's judgement is finer than the local one — is backwards for this distinction. The operator's own standing corrections in this workspace are refusals, so losing the class is not academic.

**What it does not settle.** Even a green here proves only that the distinction survives the deletion mechanically. Whether a channel governed entirely by an upstream flag stays trustworthy when that upstream changes is a judgement about a dependency nobody here versions, and no spec run today can see the version that breaks it.
