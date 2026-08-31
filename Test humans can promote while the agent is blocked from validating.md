---
type: AssumptionTest
status: unvalidated
source: 'INBOX:2026-07-22-dogfooding-idea.md'
created: '2026-07-25'
evidence: assertion
authorship: machine
---
#AssumptionTest #ported-from-ost-agent-vault #evidence/assertion

**Risk category: Usability (with feasibility of enforcement).** Riskiest assumption: hard-blocking agent self-validation does not obstruct legitimate human promotion — a human with real evidence can still mark a node validated easily.

**Proposed test (small, fast):** Have ~5 humans promote nodes (with evidence) via the intended path; separately attempt an agent-driven self-validation and confirm it is refused.

**Pre-committed success threshold:** 5 of 5 humans promote without friction; agent self-validation blocked 100% of the time.

_Proposal only — a human runs/reviews this. Unvalidated._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule

## Issues
- 2026-08-31 2026-08-31 unattended sweep, repo sight held — the mechanical half of this test's threshold is ALREADY BUILT AND GREEN, so no honest instrument can be written for it, and this node should stop being read as owing one. `test/security/self-validation.test.ts` was read in full this pass and asserts both halves of "agent self-validation blocked 100% of the time": `validated` is absent from the status enum of both `ost_create_node` and `ost_set_status` (schema assertion, so it reddens if someone re-adds the value rather than only when behaviour changes); the wire call is refused by `validateToolInput` before `run`; `run` refuses it again for an in-process caller and names `ost-agent promote` in the message; the `#unvalidated` stamp is applied server-side and survives every allowlisted tool; and `checkInvariants` still fires `no-self-validation` on a node planted from outside the surface, with a negative control proving the rule does not fire on the marker alone. The human half is asserted too — `promoteNode` clears the marker, leaves other tags, keeps `status: validated`, is idempotent, and refuses an unattributed or unexplained promotion. An instrument naming that spec would PASS today, which the ruleset forbids: a command that cannot fail measures nothing and hands a builder no definition of done. What is genuinely left is the part that spec cannot reach and this node's own threshold names first — "5 of 5 humans promote WITHOUT FRICTION". Friction is a person's report, not an exit code, and no assertion in that file observes anybody. So this is a humans-required test whose feasibility half is discharged. For a human: set the lane with `ost-agent lane --set`, since `ost_flag_humans_required` is withheld on the unattended surface, and consider whether the mechanical half's discharge is worth recording with `ost-agent result` against the narrower question. Counted alongside three others of the same shape under "Work I already finished keeps coming back in the queue, so the pass can never say it is done". Nothing else about this node changed; no instrument was set and no rung moved.
