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
[[The host scheduler leaves a readable record of a firing it was due to start and did not]]

**Variation dimension: bought-vs-built. Position taken: adopt the operating system's scheduler as the authority on whether a job ran, and build only a reader.**

The thing that was supposed to start the firing already keeps records of whether it did. On this host that is launchd, which logs each job's launches and exit statuses; elsewhere it is cron's mail and logs, or a systemd timer, which additionally carries `OnFailure=` and `systemctl list-timers` reporting last-run and next-run directly. Adopt whichever is present as the source of truth and build nothing here but the code that reads it and renders it.

**Why this position and not another.** Both siblings answer "did a firing happen" by observing the *consequences* of one — a ping that arrived, or invocations in a trace. Both therefore infer a non-event from an absence, which is the weakest form of evidence and the one this node's own parent had to lean on. The scheduler is the only participant that knows the difference between a job it never started, a job it started that exited non-zero, and a job it deliberately skipped. That is a positive record of the event rather than an inference from silence, and it is the only candidate that can distinguish the causes the parent node lists as unknown.

**What it deliberately does not do.** It writes no watchdog, defines no cadence of its own, and adds no dependency that is not already running on the machine.

**What it gives up, plainly.** Portability is the whole cost, and it is large. Three platforms mean three readers and three record formats, and the tree already carries an opportunity about not being able to tell another person "just run npm install" and have it work — this makes that worse rather than better. It is also blind in one direction the siblings are not: a job the scheduler launched successfully, which then died before recording anything, reads as a healthy run. And it cannot see a gap caused by the machine being powered off, because a scheduler that is not running logs nothing about the launches it did not attempt — which, if the observed 09-04 to 09-06 gap really was a closed laptop, is precisely the case that mattered.

**What would make this the wrong pick.** If the common cause of gaps turns out to be the host being off rather than the job failing, this candidate is blind to the majority of them and the outside-party sibling is strictly better.

**Honest note on how this was ideated.** All three candidates under this opportunity were composed in one context by one author; this surface holds no grant to run independent parallel ideators. Discount their apparent distinctness accordingly.

Unvalidated. Agent-ideated 2026-09-07; a human to review.

## Issues
- 2026-09-07 2026-09-07 unattended sweep, repo sight held: examined for a missing instrument and deliberately left without one. Recording the examination because this node was ideated earlier today and carried no prior note, so the next firing meets a decision rather than a blank node. The reason is the "subject is not in this repository" kind the census on "Work I already decided needs a person comes back every pass as work I failed to do" names: the belief beneath this node — "The host scheduler leaves a readable record of a firing it was due to start and did not" — is a claim about launchd, cron and systemd, and no spec under this repository's test/ can assert what any of them retains about a launch that never happened. A spec could assert that a reader built here parses a fixture and reports a missed firing, but that would measure a fixture this project authored rather than the external record the belief is about, which is the dishonest instrument this bucket's pressure produces. The corresponding ask is already on the standing queue as "Ask someone with launchd and systemd experience what each retains about a launch that never happened", so nothing is missing except a person. What a human should do: set the lane with `ost-agent lane --set`, since `ost_flag_humans_required` is withheld on the unattended surface. Not a skipped step. Nothing else changed — no instrument set, no status changed, no rung moved.
