---
type: Assumption
source: 'agent-ideation:2026-09-07-unattended-sweep'
created: '2026-09-07'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion

**Risk category: feasibility.**

The belief, stated so it could be false: launchd — and cron and systemd timers on the other platforms this would have to cover — keeps a record, readable after the fact, that distinguishes a scheduled firing that was never started from one that started and failed.

**How it could turn out false, and the observed gap is the exact case.** A scheduler only logs what it did. If the machine was powered off from 2026-09-04 to 2026-09-06, launchd was not running either, and there is no record of three launches it declined to attempt — there is simply nothing, which is the same nothing the invocation trace shows. In that case this candidate has adopted an authority that is silent on the majority of real gaps, and its stated advantage over its siblings — a positive record of the event rather than an inference from absence — evaporates precisely when it is needed.

It could also be false for a duller reason: launchd's per-job logging on current macOS may not retain enough to reconstruct a run history days later, and the three platforms may not agree on what they keep. An adopted authority that has to be supplemented on two of three platforms is not the cheap option this candidate claims to be.

**Why this is the belief worth testing.** The candidate's whole case is bought-not-built. If the bought thing does not answer the question, what remains is three platform-specific readers and a liveness notion built here anyway — which is the sibling candidate at several times the cost.
