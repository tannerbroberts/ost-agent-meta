---
type: AssumptionTest
source: 'agent-ideation:2026-09-07-unattended-sweep'
created: '2026-09-07'
evidence: assertion
lane: humans-required
threshold: >-
  at least 2 of the 3 platforms retain a reconstructable run history
  distinguishing not-started from started-and-failed
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: feasibility, about a third-party artefact.**

**The design.** Put three questions to someone with working knowledge of the platforms, one per scheduler: after the fact, can you reconstruct that a job was due at a given time and did not start; is that distinguishable from the job starting and exiting non-zero; and is any of it still available days later under default retention. Then the question that decides this candidate rather than merely describing it: what does each scheduler retain about launches it was due to make while the machine was powered off.

**Pre-committed bar, stated before running:** at least 2 of the 3 platforms retain a reconstructable run history distinguishing not-started from started-and-failed. Below that, the adopted authority does not answer the question and this candidate collapses into its sibling with extra platform-specific code.

**A likely answer, recorded in advance so the test cannot be read as a pass whatever comes back.** The expected finding is that systemd timers do this well (`systemctl list-timers` carries last-run and next-run, and `OnFailure=` distinguishes failure), that launchd is thinner, and that all three are silent about a powered-off interval. If that is what comes back, the honest verdict is refuted on the powered-off case even where the bar is met on the other two, because the powered-off case is the one this node's parent opportunity was mapped from.

**Why a person is irreducibly the measurement.** This is a question about software that is not in this repository and cannot be imported by a spec here. It is the same shape as the Monitor and sandbox asks already standing on this tree, and it is answered by someone who knows the platforms, not by an exit code.

**What this does not settle.** Nothing about whether an operator would read or act on the result, and nothing about the two siblings. It answers only whether the record this candidate proposes to adopt exists.

Proposed only. A human runs this; this pass did not.

A person outside the building is the measurement here: The deciding artefact is the operating system's scheduler, not this repository, so no spec under test/ can reach it; it needs someone who knows what launchd, cron and systemd actually retain.
