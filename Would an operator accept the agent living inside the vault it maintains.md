---
type: AssumptionTest
source: 'agent:ideation-2026-08-02'
created: '2026-08-02'
evidence: assertion
threshold: >-
  Of three operators shown both layouts, at least 2 accept the vault-carried
  copy and can state the upgrade command unprompted. If 2 or more say they would
  not commit the agent into a repository they keep evidence in, the candidate is
  killed.
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: usability, with a desirability edge.** The assumption is that an operator would accept the agent living *inside* the vault it maintains, and would recognise `git pull` as the upgrade action without being taught it.

**Why this is the riskiest assumption under its solution.** The mechanism is easy to build and its engineering risk is near zero — a committed bundle and a pinned version. What could kill it is a person's reaction: a vault is where this product asks operators to keep their evidence and their history, and putting a build artifact in that repository may read as contamination rather than convenience. If operators refuse the layout, the candidate's whole advantage over a registry pull disappears, because the advantage was never technical.

**The test, small and fast.** Show three operators two directory layouts side by side — the agent installed beside the vault, and the agent committed inside it — with one sentence of context each and no advocacy. Ask which they would rather run, whether the second one bothers them, and what command they would type to upgrade. Fifteen minutes each, no build required; a mock directory listing is enough.

**Pre-committed bar (also in the `threshold` field):** at least 2 of 3 accept the vault-carried copy and can state the upgrade command unprompted. If 2 or more say they would not commit the agent into a repository they keep evidence in, the candidate is killed rather than redesigned.

**A standing caveat this tree must not skip.** Every node in this vault rests on founder or agent sources, and the mandate forbids climbing the ladder on those alone. Three operators means three people who are not the founder; run with the founder as one of the three and the result is not evidence, it is the same voice again.

**What it deliberately does not cover:** it tests the layout's acceptability, not fork drift, which is this candidate's real long-run failure mode and cannot be seen in a fifteen-minute reaction. A supported result licenses building, not believing the drift problem away.
