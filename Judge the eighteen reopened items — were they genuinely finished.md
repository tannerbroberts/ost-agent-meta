---
type: AssumptionTest
source: 'agent:ideation-2026-08-03'
created: '2026-08-03'
evidence: assertion
threshold: >-
  At least 16 of the 18 reopened items are judged genuinely finished by a reader
  who is not told which build flagged them.
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: desirability — is the OR rule fixing a bug or reintroducing one?** This candidate treats an item as done if either accounting says so. That is only correct if the reopened items really were finished. If the newer build deliberately *narrowed* what counts as done — if those eighteen were genuinely incomplete under a better standard — then the fallback does not restore lost work, it re-hides real work, and it does so permanently and quietly.

**The test.** Take the eighteen items that reopened. Give a reader the evidence and the node each refers to, *without* telling them which build called them done, and ask a single question: is there anything left to do here? Blind is essential — knowing that the old build called it finished is exactly the prior that would corrupt the answer.

**Why 16 of 18.** Below that, the newer accounting is finding real gaps and the union rule would suppress them, which turns the cheapest and safest candidate in this row into the most damaging one. At or above it, the reopening is an artifact and the fallback is doing what it claims.

**This test discriminates between siblings rather than validating one idea.** A high score favours the fallback. A low score favours "Report the accounting change explicitly instead of folding it into the counts", because then the eighteen deserve a human's attention rather than automatic re-suppression — and it argues against "Migrate the old accounting into the new ledger on first run, and record that it happened" for the same reason. One question, three candidates re-ranked.

**Why a person has to answer it.** "Is there anything left to do here" is the judgement the whole accounting exists to approximate. Asking compute to grade it would be asking the disputed rule to referee its own dispute.

Proposed, not run. Recording a result is a human's `ost-agent result`.
