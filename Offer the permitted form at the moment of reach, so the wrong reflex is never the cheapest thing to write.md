---
type: Solution
created: '2026-08-05'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Measure whether the permitted wait is actually more expensive to write than the blocked one]]

**The mechanism: make the right thing the easy thing, and the memory problem dissolves.** Rather than recording the correction or forbidding the mistake, put a first-class waiting primitive where the reflex reaches. The reason `sleep 45 && gh pr checks 17` keeps getting written is that it is the shortest expression of "wait for this to finish" available; the permitted form — an until-loop under a monitor, or backgrounding the command and collecting it — is longer, less obvious, and has to be recalled. Invert that and there is nothing to remember.

**Why this shape.** It treats seven identical refusals as evidence about the *affordance*, not about the composer. A correction that has to be issued seven times is usually a sign that the thing being corrected is the path of least resistance, and no amount of memory changes which path is shortest. This is the only one of the three candidates that would also help a fresh agent, a different model, or a human operator who never saw the guard fire at all.

**Compared to its siblings.** The only one that needs no durable state and no policy — nothing to grow unbounded, nothing to over-generalise, nothing for a later session to consult. It is also the only one that improves the outcome rather than merely preventing the failure: the ledger and the constraint both end with a call not being made, while this one ends with the wait actually being done well. Its cost is that it is the most work by far, and it is speculative in a way the others are not — it assumes the reflex is driven by expression cost, and if the reflex is really driven by habit or training then a cheaper alternative sitting right there will be ignored too.

**What would make this the wrong pick.** It generalises poorly. It answers the polling case beautifully and says nothing about the other corrections in the same evidence — the shell-quoting failures, the dialect mismatches — each of which would need its own affordance designed. The ledger sibling is one mechanism for all of them; this is one mechanism per class.

⚠️ Unvalidated. Agent-ideated on 2026-08-05 from machine-captured session friction across seven sessions.
