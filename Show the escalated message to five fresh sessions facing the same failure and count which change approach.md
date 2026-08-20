---
type: AssumptionTest
source: >-
  agent-ideated:2026-08-20-unattended-sweep — the live half of "Apply the
  escalating message to the five-failure session and check where it would have
  fired", split out so one lane answers one question
created: '2026-08-20'
evidence: assertion
lane: humans-required
threshold: >-
  3 of 5 fresh sessions shown the escalated message on their second identical
  failure change approach (a different command form, a different tool, or a
  question) rather than retrying the same form a third time.
---
#AssumptionTest #unvalidated #evidence/assertion

**Kind: usability.** The half of the belief that the replay cannot touch: the counter firing is not enough, the session has to change approach when it fires.

**Design.** Five fresh sessions, each steered into the same zsh dialect failure the recorded sessions hit (`(eval):1: == not found`). On the second occurrence each is shown the escalated message — the count, the quoted first correction, the statement that it was not applied. Record what each does next and sort it: changed approach, or retried the same form.

**Why it is small.** Five sessions and a reading of five next-turns. No recruiting outside the building; the operator's own harness is the subject.

**What it will not cover.** A session shown an unusual message may change approach because it is unusual rather than because it is right, and novelty wears off; five sessions cannot see that. It also cannot tell whether the new approach is better, only that it is different.

**Relation to its sibling.** "Replay the five-failure and three-failure sessions through the class counter and require it to fire by the second occurrence in both" settles whether the counter can fire; this settles whether firing matters. Either alone leaves the solution unproven.

A person outside the building is the measurement here: A person has to run five live sessions into the same shell failure, put the escalated message in front of each, and judge whether what the session did next was a change of approach or a retry — what a caller does when shown a message is behaviour, and the repository holds none of it.
