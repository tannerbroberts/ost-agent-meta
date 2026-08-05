---
type: AssumptionTest
source: 'agent-ideation:2026-08-05-unattended-pass'
created: '2026-08-05'
evidence: assertion
threshold: >-
  Every pass writes the outcome text it ran against into its own record; two
  passes that ran against different outcome texts are distinguishable from that
  record alone, without consulting the vault's current state; and a pass whose
  outcome changed mid-run reports that rather than recording either end of it as
  though it had held throughout.
instrument: npx vitest run test/loop/goal-contract-recorded.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: feasibility.** Of this node's three clauses, two already hold and one does not, and only the third has an exit code.

**What already holds, so that the test does not claim credit for it.** *No autonomous process can alter the outcome* is enforced by construction: `ost_create_node` cannot create an Outcome at all, `ost_set_status` has no path to it, and setting one is a human's CLI call. *Any proposed change is raised as a visible question* is the ruleset's standing instruction and the only move an agent has. A spec asserting either would pass on arrival and measure nothing.

**What does not hold, and is the assumption under test.** *Every pass records which goal it ran against so drift is auditable after the fact.* Nothing writes this. The current outcome is readable from the vault at any moment, which is exactly why the gap is easy to miss: you can always see what the outcome **is**, and never what any given pass **ran against**. Those differ precisely in the window the node cares about — an outcome edited between two passes leaves both passes' records looking identical, and the drift the contract exists to make auditable is invisible in the artefact that would have to show it.

**Why the third clause is not padding.** A pass whose outcome changes mid-run is the case a naive implementation gets wrong: read the outcome once at start and stamp it, or read it once at end and stamp it, and either way the record asserts something that was not true for the whole run. Recording the change is cheap; discovering later that the stamp was a snapshot of an arbitrary moment is not.

**What is red today.** No pass record carries an outcome stamp, so clause one fails on a missing field. Clauses two and three are the ones that would go red against a first implementation, which is why all three are in one spec.

**What a green result does NOT settle, and the gap is the whole desirability half.** Whether goal drift is a fear anyone actually has — the node's own first riskiest assumption — and whether agents reliably *raise* rather than quietly reinterpret an ill-fitting goal, which is the second. Neither is touched by an audit record. The second in particular is the dangerous one and it is worth being blunt: an agent can record the exact outcome text it ran against, honestly, and still have read that text to mean something the human did not intend. A perfect audit trail of a reinterpretation is still a reinterpretation, and this instrument cannot see it. The sibling test "Unprompted-fear interviews about leaving it running" reaches the first; nothing in this tree currently reaches the second.

**And the node's own trade-off is untouched.** A locked goal that turns out to be mis-formed compounds effort in the wrong direction, and the escape hatch has to be easy for a human and impossible for the agent. That balance is a design judgement, not an exit code.

**Lane: compute-only.** Two fixture passes over a vault whose outcome is edited between them; no person is the measurement.

⚠️ Unvalidated. Agent-ideated by an unattended pass. Nothing here was run.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/loop/goal-contract-recorded.test.ts` — No test files found, exiting with code 1
