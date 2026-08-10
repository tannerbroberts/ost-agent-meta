---
type: Opportunity
source: >-
  INBOX:friction/2026-08-10-friction-pr-80-shipped-a-pass-claims-the-work-item-before.md
created: '2026-08-10'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion
[[Caller census list every shipped entry point with no in-repo caller]]
[[A shipped CLI command must appear in an automation script or be declared unwired]]

**The need, from the operator's side.** I read my changelog and my test suite and conclude a class of failure is now handled. Neither artefact can tell me whether the handling is ever reached. A module that exists, compiles, and has a green spec of its own is indistinguishable — in every record I actually look at — from one that runs. So my picture of what is protecting me is built out of things that may protect nothing.

**The instance that produced this.** PR #80 shipped `src/loop/claim.ts`, an `ost-agent claim` CLI command, and `test/cli/claim.test.ts` for the need "a pass claims the work item before it builds it". Nothing invokes it.

**Verified against the repository this pass**, which matters because the previous two passes could only take a friction filing's word for it:
- `test/cli/claim.test.ts` is present in `test/cli/`, so the unit is genuinely specified and genuinely green.
- `examples/automation/build-pass.sh` — the script that actually runs an unattended build firing — was read in full through `ost_read_repo`. It shells out to the CLI eight times: `gate`, `buildable --pending`, `verify`, `buildable`, `buildable <sol>`, `check`, `debt`, `loop health`. There is no `claim` among them.

So the claim mechanism has a spec that passes and a caller that does not exist. Its green spec is the strongest evidence available for it and it is evidence about nothing.

**Why this is the same family as its parent bucket and not a filing convenience.** The bucket's failure is a check that reports success while covering less than it claims. A sweep whose subject moved reports clean because it read nothing; a guard nothing calls reports green because it guarded nothing. Both produce a true statement about a scope that shrank to zero without anyone being told. This node's version is the one the *ledger* carries rather than the one a single run carries, which is why it is a distinct need under the same head: the sweep case is caught by counting a denominator, and no denominator exists for "was this reachable".

**More than one way to address it**, so it passes the litmus test: a reachability check at build time, a coverage-of-callers report, a smoke path that exercises every shipped entry point, or a discipline that a PR must name its caller. None of those is implied by the others.

**What this does not claim.** One instance, first-party, from the agent's own build loop. It is not evidence that operators outside this project have the same problem, and no interview supports it. Rung is the floor.

⚠️ Unvalidated. Agent-distilled from a builder-loop friction filing, corroborated against the repository by this pass.
