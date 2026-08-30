---
type: Assumption
status: unvalidated
source: >-
  tree-restructure:2026-08-05 — the belief this solution's test was already
  measuring
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion
[[Replay the seven refusals and check the ledger surfaces every one before a call is composed]]

The ledger only works if reading it precedes composing. The node names the risk itself: a reflex that survived seven explicit refusals may well survive a note about them, and a ledger that grows unbounded becomes another thing nobody reads.

## A first-party datum that deliberately does not support this belief (2026-08-30)

Recorded because the obvious reading of this pass would be a false confirmation, and saying so now is cheaper than a later pass writing "the ledger works."

**What happened.** This unattended firing's prompt carried a populated corrections ledger — three entries, listing a `Read` call refused 25 times across 20 sessions for malformed JSON, a `Bash` `sleep`-then-command form refused 10 times across 10 sessions, and one `Bash` call refused because the tool is not enabled here. The firing repeated none of them.

**Why that is not evidence for this assumption.** All three entries name tools this surface does not hold or barely uses: `Bash` is not granted on the unattended sweep at all, so two of the three refusals were unrepeatable regardless of whether anything was read. A pass cannot demonstrate that a warning changed its behaviour when the warned-about action was unavailable to it. The honest reading of this firing is **no information**, not support.

**The structural finding underneath, which is the reusable part.** The ledger is populated from refusals across *all* sessions in the workspace, but it is *read* by sessions on varying surfaces. On this surface its entire current contents were inapplicable. So the ledger as populated today cannot be tested by the unattended sweep — not because the mechanism fails, but because the sample of refusals it carries and the tool set of the reader do not overlap. Two consequences for whoever tests this:

- The test beneath this node, "Replay the seven refusals and check the ledger surfaces every one before a call is composed", should replay refusals **against a surface that actually holds the tools in question**, or it will measure availability rather than attention.
- The ledger may be worth filtering to the reading session's own granted tools. An entry a reader cannot act on is the unbounded-growth failure this node's own prose already names, arriving by a route the prose does not: not too many entries, but entries addressed to somebody else.

_Source: this firing's own prompt preamble and its own call record. Observed behaviour of this product; grounds usability, not desirability. No test was run and no result is recorded; this node's rung is unchanged at `assertion`._
