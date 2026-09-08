---
type: AssumptionTest
source: 'agent-ideation:2026-09-08-unattended-sweep'
created: '2026-09-08'
evidence: assertion
lane: humans-required
threshold: >-
  at least 3 of 3 answered yes — grant it, leave it open while unattended, and
  no revocation within 30 days
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: humans-required.**

**The question, asked in one sitting and in this order** — the order matters, because a yes to the first is cheap and a yes to the third is the one that carries:

1. Will you grant the harness's file tools read access to the product repository path?
2. Will you leave that grant open while firings run with nobody watching?
3. Thirty days from now, is it still open?

**The bar is pre-committed above and it is deliberately unanimous.** Two yeses and a revocation inside a month is a refuted verdict, not a partial success — a grant that closes is the state the tree has been in all along, and the candidate that rests on it builds nothing to survive the closure.

**Why this is the cheapest test on this branch and should be run first.** The candidate beneath which it sits builds nothing at all, so this belief is the entire mechanism: a refuted verdict retires that candidate outright and leaves the two build-something siblings as the whole option set, for the price of one conversation. A supported verdict retires *them*, because the need is answered by a permission the operator has already granted.

**What it does not settle.** Nothing about whether a search verb should exist, whether the confinement the MCP channel enforces is worth keeping, or whether the questions being asked are string questions or symbol questions. It answers one person's willingness and nothing else. In particular a yes here does not validate the candidate — it removes this candidate's largest risk, and the widened-blast-radius cost the candidate names against itself is untouched by the answer.

**Prior art on this tree, so whoever asks does not ask cold.** The operator configured `product.repos` — opening the narrower MCP channel — at some point before 2026-08-31, and left the filesystem grant shut across at least eight captured records spanning 2026-08-06 to 2026-09-08. So there is a real chance this question has already been answered by conduct, and the interview should open by checking that reading rather than by assuming the topic is new.

A person outside the building is the measurement here: Only the operator can say whether they will accept this permission posture on their own machine. It is a question about one person's risk tolerance, and no exit code can report a willingness — the grant's technical possibility is not in doubt and is not what is being asked.
