---
type: Solution
source: 'agent-ideation:2026-09-07-unattended-sweep'
created: '2026-09-07'
evidence: assertion
killIf: >-
  On the first real gap after it ships, the scheduler's own records disagree
  with the usage trace about whether a firing occurred — the adopted source
  cannot be trusted as the answer.
killBy: '2026-12-07'
authorship: machine
---
#Solution #unvalidated #evidence/assertion

**Variation dimension: bought-vs-built. Position taken: adopt the operating system's scheduler as the authority on whether a job ran, and build only a reader.**

The thing that was supposed to start the firing already keeps records of whether it did. On this host that is launchd, which logs each job's launches and exit statuses; elsewhere it is cron's mail and logs, or a systemd timer, which additionally carries `OnFailure=` and `systemctl list-timers` reporting last-run and next-run directly. Adopt whichever is present as the source of truth and build nothing here but the code that reads it and renders it.

**Why this position and not another.** Both siblings answer "did a firing happen" by observing the *consequences* of one — a ping that arrived, or invocations in a trace. Both therefore infer a non-event from an absence, which is the weakest form of evidence and the one this node's own parent had to lean on. The scheduler is the only participant that knows the difference between a job it never started, a job it started that exited non-zero, and a job it deliberately skipped. That is a positive record of the event rather than an inference from silence, and it is the only candidate that can distinguish the causes the parent node lists as unknown.

**What it deliberately does not do.** It writes no watchdog, defines no cadence of its own, and adds no dependency that is not already running on the machine.

**What it gives up, plainly.** Portability is the whole cost, and it is large. Three platforms mean three readers and three record formats, and the tree already carries an opportunity about not being able to tell another person "just run npm install" and have it work — this makes that worse rather than better. It is also blind in one direction the siblings are not: a job the scheduler launched successfully, which then died before recording anything, reads as a healthy run. And it cannot see a gap caused by the machine being powered off, because a scheduler that is not running logs nothing about the launches it did not attempt — which, if the observed 09-04 to 09-06 gap really was a closed laptop, is precisely the case that mattered.

**What would make this the wrong pick.** If the common cause of gaps turns out to be the host being off rather than the job failing, this candidate is blind to the majority of them and the outside-party sibling is strictly better.

**Honest note on how this was ideated.** All three candidates under this opportunity were composed in one context by one author; this surface holds no grant to run independent parallel ideators. Discount their apparent distinctness accordingly.

Unvalidated. Agent-ideated 2026-09-07; a human to review.
