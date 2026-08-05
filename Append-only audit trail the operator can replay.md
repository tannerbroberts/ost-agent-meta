---
type: Solution
status: unvalidated
source: 'INBOX:2026-07-22-design-goals.md'
created: '2026-07-25'
evidence: assertion
---
#Solution #ported-from-ost-agent-vault #evidence/assertion
[[Operators actually replay a history to rebuild trust, rather than just wanting one to exist]]

**Candidate solution (unvalidated).** Every change the agent makes is an atomic git commit carrying the node, its provenance link, and a human-readable message. After walking away, the operator rebuilds trust by replaying the diff history — nothing is hidden, everything is attributable to a source.

**Approach:** trust via *transparency / verifiability after the fact*.

**Contrast with siblings:** unlike the proactive digest (push) this is pull/inspect-on-demand; unlike guided-trial (earn trust before) this earns trust continuously by leaving an auditable record.

_Addresses: "Trust an unmonitored agent enough to walk away". Unvalidated — human to review._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 unlinked "Test do operators actually replay the audit trail to regain trust" — moved under "Operators actually replay a history to rebuild trust, rather than just wanting one to exist" — the belief this test measures now has a node of its own

## Definition of done

"Test do operators actually replay the audit trail to regain trust"

`npx vitest run test/git/commit-provenance.test.ts`

The spec asserts the part of this node's claim that is **not** yet true. Atomic auto-commit ships — every tool call in this sweep produced its own commit — but the messages are of the form `mcp: ost_append_to_node — appended to "<title>"`, and they name no source. The node's promise is that "everything is attributable to a source" when replaying the diff history, and today an operator reading the log alone cannot attribute anything; they have to open the vault. The spec requires the node **and** its provenance link in the commit, so it goes red against today's behaviour rather than against a missing file.

**What a green here does not settle.** Whether operators replay it at all. The node's approach is trust-via-verifiability-after-the-fact, and that bets on an act nobody has been observed performing — a complete, attributable, replayable log that no one ever opens buys exactly as much trust as no log. That is the humans-required test, and it is the one this candidate lives or dies on.
