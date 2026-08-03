---
type: AssumptionTest
source: 'agent-ideated:2026-08-03-unattended-sweep-unattended-decisions'
created: '2026-08-03'
evidence: assertion
threshold: >-
  At least 6 of the 9 held-out questions must fall into a pre-drafted class with
  no new class invented, AND at least 4 of the 9 must land in a class that says
  compute may proceed. Below 4 covered, or fewer than 2 proceed-classed, kills
  the candidate.
---
#AssumptionTest #unvalidated #evidence/assertion

**The assumption under test (feasibility):** that real forks repeat by class even though they never repeat by content. The contract only compounds if a taxonomy written before a question is asked can absorb it; if every fork is genuinely novel, the human writes a document once and the run stops just as often as before, having paid for the document.

**The test — a hold-out, so the taxonomy cannot be fitted to its own answer key.** Order the seventeen recorded `AskUserQuestion` events by timestamp. From the oldest eight, draft the decision classes and the ruling attached to each (proceed / stop-and-cite). Seal that document. Then take the nine newest, which the drafting never saw, and place each one — allowed to use only the classes already written.

**Two bars, because either one alone is gameable.** *Coverage* is how many of the nine land in an existing class without inventing a new one — a taxonomy that has to grow for every question has not generalized. *Proceed-rate* is how many land in a class that actually lets compute continue — a taxonomy that achieves perfect coverage by ruling everything stop-and-cite is a correct document that buys nothing, and it would pass a coverage-only test with full marks.

**Pre-committed before running, so this can come out a failure:** at least 6 of 9 covered with no new class, **and** at least 4 of 9 proceed-classed. Below 4 covered, or fewer than 2 proceed-classed, kills the candidate — at that point the forks are novel enough that pre-authorization is not the mechanism, and the queue or the stated-assumption sibling should be preferred. The in-between band means the contract ships narrow, covering the repeating minority and stopping on the rest, with its own coverage stated on its face.

**One class is fixed before drafting begins and is not eligible to be a proceed class:** any question about the governance of the tree itself. `TRANSCRIPT:3d729ebc-348f-4d45-8f3c-25df1de8fbc9` — *"What should the build loop do when the tree's own gate refuses a candidate?"* — is in the held-out nine, and if the drafted taxonomy places it anywhere but stop-and-cite, that is a refutation of the contract's safety, not a coverage win, and the test should be read as failed regardless of the two counts.

**Cost.** Retrospective, over transcripts already committed to this vault. No build, no operator, no external party — a session with no human present can run it end to end, provided the drafting half is genuinely sealed before the held-out half is opened.

**What it deliberately does not cover.** Whether the operator would sign the contract that comes out. A taxonomy can generalize beautifully and still describe a delegation nobody is willing to make, and no reading of past transcripts can answer that; it needs the person whose authority is being delegated.
