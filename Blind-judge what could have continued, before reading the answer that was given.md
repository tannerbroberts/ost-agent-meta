---
type: AssumptionTest
source: 'agent-ideated:2026-08-03-unattended-sweep-unattended-decisions'
created: '2026-08-03'
evidence: assertion
threshold: >-
  The blind list must agree with what the session actually did on at least 12 of
  the 17 stops, and must produce at most 2 false-independent calls across the
  whole set. Below 8 of 17, or 5 or more false-independent calls, kills the
  candidate.
instrument: npx vitest run test/loop/question-stop-independence-replay.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**The assumption under test (feasibility):** that a run can tell, at the moment it hits a fork, which of its remaining work is independent of the answer it does not have. The candidate's entire value rests on this and nothing else — a queue that banks the question is trivial to build; a queue that keeps working on the *right* things is not. The judgement has to be made in the one state where the agent has just proved it does not know the answer.

**The test.** This vault already holds seventeen `AskUserQuestion` events across nine captured transcripts. For each one, take the transcript truncated at the moment the question was asked — the answer and everything after it withheld — and write down which of the session's outstanding tasks could proceed without it. Then unseal the rest of the transcript and compare against what the session actually did once it had the answer.

Two numbers come out, and they are not equally important. **Agreement** is how often the blind list matched the real dependency structure. **False-independent calls** are the tasks the blind list said could proceed that in fact turned on the answer — these are the failure that matters, because each one is work a real run would have completed on a wrong footing and reported as finished.

**Pre-committed before running, so this can come out a failure:** at least 12 of 17 stops must agree, with no more than 2 false-independent calls across the whole set. Between 8 and 11 agreements, or 3–4 false-independents, means the queue may bank questions but must not act on its own independence judgement — it would ship as a pure stop-and-record, giving up the candidate's main claim. At or below 8 agreements, or 5 or more false-independents, kills the candidate: at that error rate the queue manufactures confidently-wrong work, which the parent opportunity is explicit is worse than stalling.

**Cost.** Retrospective, over evidence records already committed to this vault. No build, no operator, no external party, no new instrumentation — a session with no human present can run it end to end.

**What it deliberately does not cover.** Whether anyone answers a banked queue. That is the candidate's other risk and this test is silent on it by design; the tree already carries [[The whole loop waits on one human command, and nobody is told it is waiting]] for exactly that question, and duplicating it here would spend a test on ground already held. It is also silent on whether the independent work was *worth* doing — it measures correctness of the dependency call, not the value of what the call unlocked.

## History
- 2026-08-05 instrument: (none) → npx vitest run test/loop/question-stop-independence-replay.test.ts — The node's own cost paragraph already says this is settleable without a person — "Retrospective, over evidence records already committed to this vault. No build, no operator, no external party, no new instrumentation — a session with no human present can run it end to end" — and its bar is two integers over a fixed corpus: at least 12 of 17 agreements and at most 2 false-independent calls across the seventeen AskUserQuestion stops in the nine captured transcripts. The spec replays each stop with the transcript truncated at the question, has the run's own dependency classifier partition the outstanding work into can-proceed and turns-on-the-answer, unseals the remainder, and asserts both numbers against the pre-committed bar — reporting false-independents separately, because the node is explicit that those are the failure that matters. It fails today because nothing in the product classifies remaining work as dependent on an unanswered question: there is no bank-a-question write side at all (the node says so — "what does not exist is the write side"), so there is no partition for the spec to score.
